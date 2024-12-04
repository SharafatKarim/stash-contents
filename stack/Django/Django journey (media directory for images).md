---
Owner: Sharafat Karim
Last edited time: 2022-12-05T11:19
---
Let’s add our media dir. from base setting,

```Python
# Media URL's
from os import path
MEDIA_ROOT= path.join(BASE_DIR, "media")
MEDIA_URL="/media/"
```

> you can add those in the bottom

---

in the base [`urls.py`](http://urls.py) we have to now tell django to use those!

`urls.py`

```Python
from django.contrib import admin
from django.urls import include, path
from django.conf import settings
from django.conf.urls.static import static

urlpatterns = [
    path('admin/', admin.site.urls),
    path('blog/', include('blog.urls')),
    path('shop/', include('shop.urls')),
] + static(settings.MEDIA_URL,document_root=settings.MEDIA_ROOT)
```

> third and fourth line → new import