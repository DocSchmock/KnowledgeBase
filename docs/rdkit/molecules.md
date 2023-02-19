# Molecule Manipulation
## 1. Run Reactions
### Change Carbonyls to C=*
First define a reaction with SMARTS-Code:
```py
rxn = AllChem.ReactionFromSmarts('[c:1](=[O:2])>>[c:1](=[*:2])')
```
![Reaction Scheme 1](../res/rxn1.png)


If no new molecules are created, then the method `RunReactantInPlace()`can be used:
```python
m1 = Chem.MolFromSmiles('O=C1C=CNC2=C1C(=O)C=CN2')
rxn.RunReactantInPlace(m1)
```
![Reaction Scheme 2](../res/rxn2.png)

The reaction is only run **once**. If multiple exchanges need to be done, the method needs to be executed several times on the input molecule. 

``` {.py3 linenums="1"}
# For single molecule

while rxn.RunReactantInPlace(m1):
    pass

# For multiple molecules in a list or Pandas dataframe

while any(df_wC['ROMol'].map(rxn.RunReactantInPlace)):
  pass
```
![Reaction Scheme 3](../res/rxn3.png)

As alternative, dummy atoms can also be replaced without reactions. In this case one can use `Chem.ReplaceSubstructs(mol,query,subst,replaceAll=False)`
``` {.py3 linenums="1"}
sub = Chem.MolFromSmiles('C(C#N)C#N')
prods = [Chem.ReplaceSubstructs(x,Chem.MolFromSmarts('[#0]'),sub, replaceAll=True)[0] for x in df_wCend['ROMol']]
```