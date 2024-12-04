---
Owner: Sharafat Karim
Last edited time: 2022-12-05T10:59
---
First, let’s create a superuser,

`python manage.py createsuperuser`

---

now let’s register our database in admin

```Python
from django.contrib import admin

# Register your models here.
from .models import Product
admin.site.register(Product)
```

---

now time to head over to,

[http://127.0.0.1:8000/admin/](http://127.0.0.1:8000/admin/)

---

you can see your models right?

Let’s add more models,

`models.py`

```Python
from django.db import models

# Create your models here.
class Product(models.Model):
    product_id = models.AutoField
    product_name = models.CharField(max_length=50)
    category = models.CharField(max_length=50, default="")
    subcategory = models.CharField(max_length=50, default="")
    price = models.IntegerField(default=0)
    desc = models.CharField(max_length=300)
    pub_date = models.DateField()
    image = models.ImageField(upload_to="shop/images", default="")

    def __str__(self):
        return self.product_name
```

that **str**(self) method is for defining the name in your admin panel!

finally run, `makemigrations` and `migrate`

> `str(self)` method doesn’t need to be `migrate`d 🌿