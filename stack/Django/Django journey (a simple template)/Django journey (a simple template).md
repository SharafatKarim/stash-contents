---
Owner: Sharafat Karim
Last edited time: 2022-12-04T20:21
---
a new dir inside our project not our sub-project named dir.

![[/Untitled 6.png|Untitled 6.png]]

it’s called _templates!_

now, let’s add the entry in **settings.py**

```Python
TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': ['templates'],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]
```

inside the template, let’s add an HTML and link it!

```Python
from django.shortcuts import render

def index(request):
    params = {"name": "sharafat", "location": "Bangladesh"}
    return render(request, 'index.html', params)
```

here we can pass vars like _param_