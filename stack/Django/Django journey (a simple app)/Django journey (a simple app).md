---
Owner: Sharafat Karim
Last edited time: 2022-12-04T20:45
---
It’s time for an app! We’ll run,

`py manage.py startapp members`

And it’ll create a members/ directory along with it’s contents!

> We can create template like before but this time it’ll be inside of members/ directory

![[/Untitled 4.png|Untitled 4.png]]

# Basic

it’s `urls.py`

```Python
from django.urls import path
from . import views

urlpatterns = [
    path('', views.index, name='index'),
]
```

and, `views.py`

```Python
from django.http import HttpResponse
from django.template import loader

def index(request):
  template = loader.get_template('myfirst.html')
  return HttpResponse(template.render())
```

it should work now!

# Integration

![[Untitled 1.png]]

access it’s setting and add the app, like,

```Python
# Application definition

INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'members.apps.MembersConfig'
]
```

umm, `members.apps.Members`?

![[/Untitled 2 2.png|Untitled 2 2.png]]

finally, execute,

`python manage.py migrate`

---

Just putting the appname instead of `app.apps.appconfig` also works without `migrate`

---

and in the root `urls.py`

```Python
from django.urls import include, path
path('members/', include('members.urls')),
```