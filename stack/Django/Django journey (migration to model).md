---
Owner: Sharafat Karim
Last edited time: 2022-12-04T21:33
---
First, let’s finish our migration,

in terminal,

`python manage.py migrate`

---

Now it’s time to create model,

head over to,

[models.py](http://models.py) and create one,

```Python
from django.db import models

# Create your models here.
class Product(models.Model):
    product_id = models.AutoField
    product_name = models.CharField(max_length=50)
    desc = models.CharField(max_length=300)
    pub_date = models.DateField()
```

for reference,

> [!info] Django  
> A file-upload field.  
> [https://docs.djangoproject.com/en/4.1/ref/models/fields/](https://docs.djangoproject.com/en/4.1/ref/models/fields/)  

---

make sure, your app in the setting like this,

```Python
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'blog.apps.BlogConfig',
    'shop.apps.ShopConfig',
]
```

last 8/9th line

---

then execute,

`python manage.py makemigrations`

and finally,

`python manage.py migrate`