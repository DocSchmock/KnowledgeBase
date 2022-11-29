# The Plotting Cookbook

## 1. Scatterplot with Linear Regression (Correlation)
```python
import matplotlib.pyplot as plt
import seaborn as sns
from scipy import stats
fig = plt.figure(figsize=(8,8))
sns.set_theme(style='whitegrid', rc={'grid.linestyle': '--'})
ax = sns.regplot(data=df_merged, x='LLo', y='LGxtb')
ax.set(ylabel='LUMO XTB_def2-TZVP_gas', xlabel='LUMO XTB_SDC Method_gas', title='High Lvl vs Lo Lvl of Theory')
slope, intercept, r_value, p_value, std_err = stats.linregress(df_merged.LLo, df_merged.LGxtb)
r2 = r_value**2
txt = f'Slope: {slope}, \nIntercept: {intercept} \n r2: {r2}'
ax.annotate(txt, xy=(-6, -3))
```

## 2. Scatterplot with Reference, Labeling and Box
```python
import matplotlib.pyplot as plt
import seaborn as sns
import matplotlib.patches as mpatches
fig = plt.figure(figsize=(8,8))
fig, ax = plt.subplots(figsize=(8,8))
sns.set_theme(style='whitegrid', rc={'grid.linestyle': '--'})
ax1 = sns.scatterplot(data=df_merged, x='Lhf', y='Ghf', marker="$\circ$", ec="face")
sns.scatterplot(data=ref, x='LUMO', y='GAP', hue='Name', marker='*', s=200)
rect=mpatches.Rectangle((-5.5,3),1,0.6, 
                        fill = False,
                        color = "teal",
                        linewidth = 1.5,
                        linestyle='--')
	
plt.gca().add_patch(rect)
for i, language in enumerate (df_merged.lfd):
    plt.annotate(language, (df_merged.Lhf[i]+0.03, df_merged.Ghf[i]), size='xx-small')

ax.set(ylabel='GAP hf3c_def2-TZVP_gas [eV]', xlabel='LUMO hf3c_def2-TZVP_gas [eV]', title='New Heterocyclic Cores Prescreening')

plt.savefig('filter.png', dpi=300, bbox_inches='tight')
plt.show()
```
