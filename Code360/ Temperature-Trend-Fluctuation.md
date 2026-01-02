# Temperature Trend Fluctuation

## Problem Statement
Dr. Ninja, a climate scientist, is studying a dataset of daily average temperatures to identify patterns of weather volatility. He is particularly interested in moments where the temperature trend makes a significant shift, which she calls a "trend fluctuation".



A trend fluctuation occurs on a given day if the temperature trend leading up to that day (e.g., warming) reverses direction on the following day (e.g., cooling).



You are given a list of daily temperatures. Your task is to help Dr. Ninja by calculating the total number of trend fluctuations in the dataset.


---

##  Approach

- Use simple for loop and if else for solving.
- but, for handling duplicates. Think by yourself.
---

## Time Complexity
    O(n)
---

## Space Complexity

    O(1)
---
## Note
    Just dry run.
---

## Python Solution

```python
from typing import List

def count_fluctuations(temp: List[int]) -> int:
    a=temp
    fluc=0
    for i in range(1,len(a)-1):
        if a[i]==a[i+1]:
            a[i]=a[i-1]
        if (a[i-1]>a[i] and a[i]<a[i+1]) or (a[i-1]<a[i] and a[i]>a[i+1]) :
            fluc+=1
    return fluc
