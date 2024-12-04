---
Owner: Sharafat Karim
Last edited time: 2022-12-04T18:09
---
For a single input just input function is enough!

```Python
input()
```

but for the input that you don’t know how much long?

It’s called taking input until EOF!

```Python
import sys


user_input = sys.stdin.read()

print(user_input)
```

---

more @[https://bobbyhadz.com/blog/python-read-input-until-eof](https://bobbyhadz.com/blog/python-read-input-until-eof)