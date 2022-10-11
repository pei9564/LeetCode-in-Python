# 7 kyu

## Distance from the average (10/11)

```
# Mine

def distances_from_average(test_list):

    mean = sum(test_list) / len(test_list)
    return [round(mean - i, 2) for i in test_list]
```

```
# Best answer

from numpy import mean

def distances_from_average(test_list):
    avg = mean(test_list)
    return [round(avg - x, 2) for x in test_list]
```

## Pandas Series 101: Rename Columns (10/11)

```
# Mine

import pandas as pd

def rename_columns(df, names): 
    result = df.copy()
    result.columns = names
    return result
```

```
# Best answer

import pandas as pd

def rename_columns(df, names):  
    return pd.DataFrame(data=df.values, columns=names)
```
