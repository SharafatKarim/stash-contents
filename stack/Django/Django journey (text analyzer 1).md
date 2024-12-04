---
Owner: Sharafat Karim
Last edited time: 2022-12-02T10:29
---
umm, let’s create an another page, in URL,

```Python
path('removepunc/', views.removepunc, name="Remove punctuation"),
```

and add a textarea and a button to submit to the HTML (index.html)

```HTML
<form action="/removepunc" method="get">
      <textarea name="text" style="width: 100%; height: 158px;">
      </textarea>
      <button type="submit">Analylze text</button>
</form>
```

now, text action will go to “/_removepunc_” address

`http://127.0.0.1:8000/removepunc/?text=yo`

  

let’s catch the text,

```Python
def removepunc(request):
    print(request.GET.get('text', 'default'))
    return HttpResponse("<h1>Removing punctuation</h1>")
```

now, we’ll get the input in the terminal!