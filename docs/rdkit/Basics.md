# Basics
## 1. Templates for Data Science
### Standard Imports
~~~py
import pandas as pd
from rdkit import Chem
from rdkit.Chem import PandasTools, Draw, rdDepictor, rdMolDescriptors, Fragments
from rdkit.Chem.Draw import IPythonConsole
import datamol as dm
IPythonConsole.molSize = 300,300
rdDepictor.SetPreferCoordGen(True)
~~~

## Miscellaneous
### Use Anaconda / rdkit in Google Colab
Enabling conda package manager for Google Colabs
~~~py
!pip install -q condacolab
import condacolab
condacolab.install()
!conda install -c rdkit rdkit
!conda install datamol
~~~
~~~
⏬ Downloading https://github.com/jaimergp/miniforge/releases/latest/download/Mambaforge-colab-Linux-x86_64.sh...
📦 Installing...
📌 Adjusting configuration...
🩹 Patching environment...
⏲ Done in 0:00:23
🔁 Restarting kernel...
~~~
