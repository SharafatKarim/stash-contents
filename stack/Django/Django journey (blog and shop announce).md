---
Owner: Sharafat Karim
Last edited time: 2022-12-04T20:55
---
First of all, let’s setup 2 different app

- blog
- shop

---

after setting up, let me share the `shop` directory’s some content

urls.py

```Python
from django.urls import path
from . import views

urlpatterns = [
    path('', views.index, name='index'),
]
```

---

and it’s `views.py`

```Python
from django.shortcuts import render

# Create your views here.
from django.http import HttpResponse
from django.template import loader

def index(request):
  template = loader.get_template('shop/index.html')
  return HttpResponse(template.render())
```

and I’ll set a HTTP template at,

`/supersite/shop/templates/shop/index.html`