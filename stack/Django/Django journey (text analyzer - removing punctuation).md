---
Owner: Sharafat Karim
Last edited time: 2022-12-02T10:29
---
first stop! let’s tweak HTML to read one text data and one checkbox (optional)

```HTML
<form action="/analyze" method="get">
      <textarea name="text" style="width: 50%; height: 158px;">
      </textarea><br>
      <input type="checkbox" name="removepunc"> Remove Punctuation <br>
      <button type="submit">Analylze text</button>
</form>
```

and of course the landing page,

just some shortcuts like `{{shortcuts}}`

```HTML
    Here's your {{purpose}} text!
    <p>
    {{analyzed}}
    </p>
```

simple! right?

then a function to remove punctuation!

and we’ll integrate with our manually created function!

```Python
...
from django.shortcuts import render
from string import punctuation

...
def analyze(request):
    djtext = request.GET.get('text', 'default')
    removepunc = request.GET.get('removepunc', 'off')

    analyzed = ""
    for char in djtext:
        if char not in punctuation:
            analyzed += char

    print(djtext)
    print(analyzed)

    params = {"analyzed":analyzed, "purpose":"punctuation removed"}
    return render(request, 'analyze.html', params)
```

> I didn’t bother to use `removepunc` var (values: on | off), feel free to do so

and finally the pipeline,

`path('analyze/', views.analyze, name="Analyze text"),`

it’s pretty much simple!