---
Owner: Sharafat Karim
Last edited time: 2022-12-04T11:46
---
Create a static directory, (not statics, i guess)

then, in the html, just use,

```HTML
{% load static %}
<img src="{% static 'my_app/example.jpg' %}" alt="My image">
```

or, similar

```HTML
{% load static %}
  <a href="{% static 'blog/blog.txt' %}">Click here!</a>
```

---

more @[https://docs.djangoproject.com/en/4.1/howto/static-files/](https://docs.djangoproject.com/en/4.1/howto/static-files/)