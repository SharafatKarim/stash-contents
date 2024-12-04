---
Owner: Sharafat Karim
Last edited time: 2022-12-04T21:02
---
let’s extend our shop a bit with URLs

```Python
from django.urls import path
from . import views

urlpatterns = [
    path('', views.index, name='index'),
    path('about/', views.about, name='AboutUs'),
    path('contact/', views.contact, name='contact'),
    path('tracker/', views.tracker, name='tracker'),
    path('search/', views.search, name='search'),
    path('productview/', views.productview, name='ProductView'),
    path('checkout/', views.checkout, name='checkout'),
]
```

---

and our views

```Python
from django.shortcuts import render

# Create your views here.
from django.http import HttpResponse
from django.template import loader

def index(request):
  template = loader.get_template('shop/index.html')
  return HttpResponse(template.render())

def about(request):
  return HttpResponse("We are at about")
def contact(request):
  return HttpResponse("We are at contact")
def tracker(request):
  return HttpResponse("We are at tracker")
def search(request):
  return HttpResponse("We are at search")
def productview(request):
  return HttpResponse("We are at productview")
def checkout(request):
  return HttpResponse("We are at checkout")
```