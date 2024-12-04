---
Owner: Sharafat Karim
Last edited time: 2022-11-22T10:37
---
```Python
from numba import njit


@njit
def counter(n):
    print(n)
    while n != 10000000000:
        n += 1
    return n


print(counter(0))
```