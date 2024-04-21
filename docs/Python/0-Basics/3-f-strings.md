#  f-string tricks

F-strings are faster than the other string formatting methods and are easier to read and use.
Here are some tricks you may not have known.

### 1. Number formatting :
You can do various formatting with numbers.
```py
>>> number = 150

>>> # decimal places to n -> .nf
>>> print(f"number: {number:.2f}")
number: 150.00

>>> # hex conversion
>>> print(f"hex: {number:#0x}")
hex: 0x96

>>> # binary conversion
>>> print(f"binary: {number:b}")
binary: 10010110

>>> # octal conversion
>>> print(f"octal: {number:o}")
octal: 226

>>> # scientific notation
>>> print(f"scientific: {number:e}")
scientific: 1.500000e+02

>>> # total number of characters
>>> print(f"Number: {number:09}")
Number: 000000150

>>> ratio = 1 / 2
>>> # percentage with 2 decimal places
>>> print(f"percentage = {ratio:.2%}")
percentage = 50.00%
```
### 2. Stop writing print(f”var = {var}”)
This is the debug feature with f-strings.
This is known as self-documenting expression released in Python 3.8 .

```py
>>> a, b = 5, 15
>>> print(f"a = {a}") # Doing this ?
a = 5
>>> # Do this instead.
>>> print(f"{a = }")
a = 5
>>> # Arithmatic operations
>>> print(f"{a + b = }")
a + b = 20
>>> # with formatting
>>> print(f"{a + b = :.2f}")
a + b = 20.00
```
### 3. Date formatting
You can do `strftime()` formattings from f-string.
```py
>>> import datetime

>>> today = datetime.datetime.now()
>>> print(f"datetime : {today}")
datetime : 2023-10-27 11:05:40.282314

>>> print(f"date time: {today:%m/%d/%Y %H:%M:%S}")
date time: 10/27/2023 11:05:40
>>> print(f"date: {today:%m/%d/%Y}")
date: 10/27/2023
>>> print(f"time: {today:%H:%M:%S %p}")
time: 11:05:40 AM
```
Check [more formatting options](https://docs.python.org/3/library/datetime.html#strftime-and-strptime-format-codes).

#### Thank you for reading!
#python