---
Owner: Sharafat Karim
Last edited time: 2022-12-08T20:30
---
A simple text file

and we want to sync update from GitHub,

---

```Python
from filecmp import cmp
import os

def autoupdate_hook():
    if os.getcwd() == os.getenv("HOME"):
        os.system('curl -s --output "$PWD/lazypac_updated.py" "https://raw.githubusercontent.com/redwan-hossain/lazypac/main/lazypac.py"')
        if not cmp("lazypac.py", "lazypac_updated.py"):
            os.system("mv lazypac_updated.py lazypac.py")
            print("Script has been updated!")
        else:
            os.system("rm lazypac_updated.py")

autoupdate_hook()
```

corresponding repository, [https://github.com/redwan-hossain/lazypac](https://github.com/redwan-hossain/lazypac)