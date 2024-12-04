---
Owner: Sharafat Karim
Last edited time: 2022-12-05T18:18
---
To get started in the shell, execute,

`python manage.py shell`

---

shell looks beautiful, right?

![[/Untitled 3.png|Untitled 3.png]]

---

to access `DateField()` import `timezone`

```Python
from django.utils import timezone
```

and also import like this,

```Python
Prod = Product(product_name='keyboard',category='key',subcategory='',price=150,de
    ...: sc='somehting that we use daily', pub_date= timezone.now())
```

And finally,

```Python
Prod.save()
```

You can list all by, `Product.objects.all()`

And even more at it’s documentations, good luck!