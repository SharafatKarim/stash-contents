---
Owner: Sharafat Karim
Last edited time: 2022-12-04T11:12
---
```Python
# Python program to illustrate
# enumerate function in loops
l1 = ["eat", "sleep", "repeat"]

# printing the tuples in object directly
for ele in enumerate(l1):
	print (ele)

# changing index and printing separately
for count, ele in enumerate(l1, 100):
	print (count, ele)

# getting desired output from tuple
for count, ele in enumerate(l1):
	print(count)
	print(ele)
```

> [!info] Enumerate() in Python - GeeksforGeeks  
> Often, when dealing with iterators, we also get need to keep a count of iterations.  
> [https://www.geeksforgeeks.org/enumerate-in-python/](https://www.geeksforgeeks.org/enumerate-in-python/)