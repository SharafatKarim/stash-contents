---
Owner: Sharafat Karim
Last edited time: 2022-12-05T14:44
---
First if you need a `requirements.txt` then, try installing,

`pip install pipreqs`

then, running, `pipreqs` or `pipreqs .` in the directory may do the trick!

> `pipreqs` and `pipreq` are not same. `pipreq` will print every single installed packages, I guess!

---

to install from `requirements.txt` then, execute,

`pip install -r requirements.txt`

---

for real time creation,

first we can run `pipreqs`

then enter virtual environment `venv`

chances are, `pipreqs` won’t grab everything

so then install the rests according to your terminal!

finally, execute `pipreq` (not `pipreqs`)

you’ll get the final `requirements.txt`