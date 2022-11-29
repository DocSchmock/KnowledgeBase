# The Pandas Cookbook

## 1. Join multiple dataframes on column
```python
from functools import reduce
df_merged = reduce(lambda  left,right: pd.merge(left,right,on=['lfd'],
                                            how='outer'), [xtbgas2, xtbdcm2, hf3cgas2,  xtbgauss2])
```