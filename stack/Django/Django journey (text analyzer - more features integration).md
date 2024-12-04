---
Owner: Sharafat Karim
Last edited time: 2022-12-02T10:29
---
Now we can add more features!

And don’t forget to add a radio button on the html so that one request at a time!

```HTML
<form action="/analyze" method="get">
      <textarea name="text" style="width: 50%; height: 158px;">
      </textarea><br>
      <input type="radio" name="choice" value="removepunc"> Remove Punctuation <br>
      <input type="radio" name="choice" value="capitalize"> UPPERCASE <br>
      <input type="radio" name="choice" value="newlinestrip"> One Liner<br>
      <input type="radio" name="choice" value="extraspacestrip"> Extra space remove<br>
      <input type="radio" name="choice" value="wordcount"> Word count<br>
      <button type="submit">Analylze text</button>
    </form>
```

then, we just have to make sure, our [_views.py_](http://views.py) can actually read it!

```Python
def analyze(request):
    djtext = request.GET.get('text', 'default')
    choice = request.GET.get('choice')
    analyzed = ""
    purpose = ""

    match choice:
        case "removepunc":
            prupose = "punctuation removed"
            for char in djtext:
                if char not in punctuation:
                    analyzed += char
        case "capitalize":
            prupose = "punctuation removed"
            for char in djtext:
                analyzed += char.upper()
        case "newlinestrip":
            purpose = "new line removed"
            for char in djtext:
                if char == "\n":
                    analyzed += " "
                    continue
                analyzed += char
        case "extraspacestrip":
            purpose = "extra space removed"
            for index, char in enumerate(djtext):
                if djtext[index] == " " and djtext[index+1] == " ":
                    pass
                analyzed += char
        case "wordcount":
            purpose = "words counted"
            analyzed = count_word_from_text(djtext)
        case _:
            return HttpResponse("<h1>Invalid Choice!</h1>")

    params = {"analyzed":analyzed, "purpose": purpose}
    return render(request, 'analyze.html', params)
```

and don’t forget the `count_word_from_text()` function!

```Python
def count_word_from_text(text):
    text = text.strip("\n").strip(" ")
    count= 1
    previous_new_line = 0
    for i in text:
        if i == " ":
            count += 1
            previous_new_line = 0
        elif i == "\n" and previous_new_line == 0:
            count += 1
            previous_new_line = 1
        elif i == "\n" and previous_new_line == 1:
            previous_new_line = 1
        elif i == "\t":
            count += 1
            previous_new_line = 0
        else:
            previous_new_line = 0
    return count
```