# Python Paramiko tutorial

I recently had a task that required me to connect to an SFTP server, download particular files (if they existed), and then process the contents. We were given the option of using any language to fulfil the criteria, so I chose Python to tackle the problem. This blog outlines the problems I encountered when attempting to build the script, as well as a tutorial on how to use the library.

[This](https://stackoverflow.com/questions/48434941/pysftp-vs-paramiko) StackOverflow answer lists the differences between the libraries.

We need to have some version of python installed in our machine to use the library, in my case I am currently using `python 3.8`.

Run the following command in the terminal to install the `paramiko` library globally

```zsh
pip install paramiko
```

It is suggested that we have an SFTP server up and running in order to test the script. Our server can assist us in configuring the setup to our liking.

If you do not want to set up or have an SFTP server to test on, we can utilise several publicly available servers. A list of servers may be found [here](https://www.sftp.net/public-online-sftp-servers).

Now let's start discussing how to use the library. We'll be talking about the following in upcoming sections.

* Connecting to the remote server
* Executing commands on the server
* Transferring files (Upload/Download)
* The final script

⠀
First let's define the constants for connection properties like hostname, username, password, public key, private key etc.., In a real-world application, these properties should come from a configuration file/system.

```py
HOST_NAME = "test.rebex.net"
USER_NAME = "demo"
PASSWORD = "password"
PRIVATE_KEY_FILE = '/some/file/path/private_key.txt'
PORT = 22
```

To connect to the server we create an instance `client` of `paramiko.SSHClient()`. [Paramiko.SSHClient](https://docs.paramiko.org/en/stable/api/client.html) is the primary class used to make connections to the remote server and execute commands. This class wraps [Transport](https://docs.paramiko.org/en/stable/api/transport.html), [Channel](https://docs.paramiko.org/en/stable/api/channel.html), and [SFTPClient](https://docs.paramiko.org/en/stable/api/client.html#paramiko.client.SSHClient) to take care of most(not all as discussed below) aspects of authenticating and opening channels. The creation of an SSHClient object allows establishing server connections via the [`connect()`](https://docs.paramiko.org/en/stable/api/client.html#paramiko.client.SSHClient.connect) method.

```py
client = paramiko.SSHClient()
client.connect(hostname=HOST_NAME, port=PORT, username=USER_NAME, password=PASSWORD)
```

[`connect()`](https://docs.paramiko.org/en/stable/api/client.html#paramiko.client.SSHClient.connect) method has support for a wide variety of ways to authenticate before connecting to the server for a user. The above-mentioned method is for password-based authentication.

For private key-based auth, instead of passing the password parameter, we can instead pass `pkey` an object of type [PKey](https://docs.paramiko.org/en/stable/api/keys.html#paramiko.pkey.PKey) or `key_filename` the list of private key file names.

```py
client = paramiko.SSHClient()
pkey = paramiko.RSAKey.from_private_key_file(PRIVATE_KEY_FILE)
client.connect(hostname=HOST_NAME, port=PORT, username=USER_NAME, pkey=pkey)

client = paramiko.SSHClient()
client.connect(hostname=HOST_NAME, port=PORT, username=USER_NAME, key_filename=PRIVATE_KEY_FILE)
```

However, [`connect()`](https://docs.paramiko.org/en/stable/api/client.html#paramiko.client.SSHClient.connect) method doesn't support 2-Factor authentication. Following are a few examples where the above method might not work.

* SFTP server is enabled with both password and private key-based auth.
* SFTP server needs an OTP post entering the password to login into the server.

⠀
For use cases like these instead of creating an object of [Paramiko.SSHClient](https://docs.paramiko.org/en/stable/api/client.html) we can create [Paramiko.Transport](https://docs.paramiko.org/en/stable/api/transport.html) instead. Transport method has a support to authenticate the connection after successful negotiation by the methods like [auth_password](https://docs.paramiko.org/en/stable/api/transport.html#paramiko.transport.Transport.auth_password), [auth_publickey](https://docs.paramiko.org/en/stable/api/transport.html#paramiko.transport.Transport.auth_publickey), [auth_interactive](https://docs.paramiko.org/en/stable/api/transport.html#paramiko.transport.Transport.auth_interactive) etc..,

Following are a few sample code snippets for the usage of above mentioned methods

```py
transport = paramiko.Transport()
transport.start_client()
transport.auth_password(USER_NAME, PASSWORD)
pkey = paramiko.RSAKey.from_private_key_file(PRIVATE_KEY_FILE)
transport.auth_publickey(USER_NAME, pkey)
```

Here we use [`auth_interactive`](https://docs.paramiko.org/en/stable/api/transport.html#paramiko.transport.Transport.auth_interactive) method which accepts a handler for passing the values to the prompt. The custom handler that we write has the logic to pass the OTP or Password etc.. based on the output in the prompt. If we want to get the input to the handler from `stdin` instead then we can use the [`auth_interactive_dumb`](https://docs.paramiko.org/en/stable/api/transport.html#paramiko.transport.Transport.auth_interactive_dumb) method.

```py
transport = paramiko.Transport()
transport.start_client()
transport.auth_interactive(username, handler) def handler(self, title, instructions, prompt_list): answers = [] for prompt_, _ in prompt_list: prompt = prompt_.strip().lower() if prompt.startswith('password'): answers.append(PASSWORD) elif prompt.startswith('verification'): answers.append(OTP) else: raise ValueError('Unknown prompt: {}'.format(prompt_)) return answers
```

After we have successfully logged into the server by any one of the above-mentioned methods executing the commands is as simple as passing your command to [exec_command](https://docs.paramiko.org/en/2.9/api/client.html#paramiko.client.SSHClient.exec_command).

```py
command = "ls -l"
stdin, stdout, stderr = client.exec_command(command)
print(stdout.read())
```

However paramiko has some very useful util methods to run SFTP commands on the server, following are a few of them

```py
sftp_client = client.open_sftp()
sftp_client.chdir() 
sftp_client.cwd() 
sftp_client.listdir()
```

For other supported commands, we can refer to [this documentation](https://docs.paramiko.org/en/stable/api/sftp.html).

Paramiko allows to programmatically send and receive files using the SFTP protocol. To upload/download file we need to create an [`SFTPClient`](https://docs.paramiko.org/en/stable/api/sftp.html#paramiko.sftp_client.SFTPClient) session object by calling [`open_sftp()`](https://docs.paramiko.org/en/stable/api/client.html?highlight=open_sftp#paramiko.client.SSHClient.open_sftp). This object allows to perform common SFTP operations like [`get()`](https://docs.paramiko.org/en/stable/api/sftp.html#paramiko.sftp_client.SFTPClient.get), [`put()`](https://docs.paramiko.org/en/stable/api/sftp.html#paramiko.sftp_client.SFTPClient.put).

```py
sftp_client= client.open_sftp()
sftp_client.put(uploadlocalfilepath,uploadremotefilepath)
sftp_client.close()
```

```py
sftp_client= client.open_sftp()
sftp_client.get(downloadremotefilepath,downloadlocalfilepath)
sftp_client.close()
```

Navigate to [this link](https://gist.github.com/me-manikanta/aa9e0fd11ba2757521b6e1c5265ac29a#file-paramiko_example-py) for the gist of the following script. Star ⭐️ the gist if it helped you.

[Python Paramiko tutorial](https://manicodes.hashnode.dev/how-to-python-paramiko)