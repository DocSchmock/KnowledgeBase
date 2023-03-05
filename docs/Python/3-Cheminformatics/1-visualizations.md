# Visualizations
## Orbitals
As an alternative to PyMol the python package `py3Dmol`can be used:
~~~{.py3 linenums="1"}
import py3Dmol

v = py3Dmol.view()
v.addModel(Chem.MolToMolBlock(mol), 'mol')
v.setStyle({'stick':{}})

def draw_orbital(view, i):
    with open(f"./benzene_nao_{i:02d}.cube") as f:
        cube_data = f.read()
    view.addVolumetricData(cube_data, "cube", {'isoval': -0.04, 'color': "red", 'opacity': 0.75})
    view.addVolumetricData(cube_data, "cube", {'isoval': 0.04, 'color': "blue", 'opacity': 0.75})
    view.addModel(Chem.MolToMolBlock(mol), 'mol')
    view.setStyle({'stick':{}})
    view.zoomTo()
    view.update()
    view.clear()

view = py3Dmol.view(width=400,height=400)
view.show()
draw_orbital(view, 25)

~~~