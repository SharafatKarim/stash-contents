---
Owner: Sharafat Karim
Last edited time: 2022-12-02T10:45
---
post will hide url and allow you more data input and more security!

but won’t allow you to just go ahead and share direct URL!

in the html, try,

```JavaScript
<form action='/analyze' > {% csrf_token%}
```

now, what is this `csrf` thing? maybe a google search!

and, then replace “GET” with “POST” in your `views.py`

```Python
djtext = request.POST.get('text', 'default')
```

and another think, it’ll be hard to use `newline-remover` now, cause you also have to consider `\r`

so, code will be like,

```Python
if char != "\n" and char!="\r":
	pass
```

> maybe I should share the full instance

```Python
if (newlineremover == "on"):
        analyzed = ""
        for char in djtext:
            if char != "\n" and char!="\r":
                analyzed = analyzed + char
```