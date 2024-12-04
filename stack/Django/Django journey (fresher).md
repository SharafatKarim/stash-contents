---
Owner: Sharafat Karim
Last edited time: 2022-12-02T10:30
---
Installed it

```Bash
pip install django
```

created a server/ whatever

```Bash
django-admin startproject mysite
```

I ran the server

```Bash
python manage.py runserver
```

> fun fact: the tab completion was working all the way in terminal

created a file manually called “_views.py_” inside _project-name_ directory.

then, created 2 different pages using “_views.py”_

```Python
# A file created manually!
from django.http import HttpResponse

def index(request):
    return HttpResponse("hello")

def about(request):
    return HttpResponse("<h1>About Sharafat</h1>")
```

also linked this with the support of urls.py

```Python
from . import views

urlpatterns = [
    path('admin/', admin.site.urls), \#default line
    path("", views.index, name="index"),
    path("about/", views.about, name="about"),
]
```