# NESTED


## Nested Serializer haqida

Nested serializerdan biz foydalanmiz qachonki, bizga biror object ichida boshqa realtion bo'lgan objectning fieldlarini to'ldirishda foyalanamiz


<p align="center">
    <br>
    <img src="src/programming-languages.gif" alt="List of programming languages logos">
    <br>
    <br>
    <br>
    <br>
    <!-- 
        Plese don't fix the world 'porgramming' it is not a typo.
        Well it is a typo but a working typo :) 
    -->
    <img src="https://cdn.abranhe.com/projects/porgramming-languages-logos/logo.svg" alt="programming gif">
    <br>
    <br>
   <b>NESTED SERIALIZER</b>
    <br>
    <br>
    <a href="https://languages.abranhe.com"><code>languages.abranhe.com</code></a>
</p>

<p align="center">

<img src="https://i.stack.imgur.com/FW9Qe.png" alt="Some programming languages logos">
</p>

### models.py fayliga 2 taqo'yidagicha modulyaratamiz
* models.py
  ```sh
    from django.db import models
    
    class Category(models.Model):
        title=models.CharField(max_length=50)
    
    class Ads(models.Model):
        category=models.ForeignKey(Category,on_delete=models.CASCADE,related_name='category')
        title=models.CharField(max_length=40)
  ```

### yaratga appimizdi settings.py fayliga qo'shib bazani makemigrations va migrate qilamiz
* create baza
```
python manage.py makemigrations
python manage.py migrate
```


### serializer.py nomli fayl yaratamiz
* serializer.py

```sh
from .models import Ads,Category
from rest_framework import serializers


class CategorySerializer(serializers.ModelSerializer):
    class Meta:
        model=Category
        fields='__all__'

class AdsSerializer(serializers.ModelSerializer):
    category=CategorySerializer()   # nested serializer 

    class Meta:
        model=Ads
        fields='__all__'
```

  yuqoridagi codenning modile.py fayliga etibor bering, Catgory nomlli modulni Ads nomli modulga ForiegnKey fields sifatida category o'zgaruvchisagi saqlaganmiz, shu qaysidir catrgorygategishli barcha objectlarning saqlash yoki ko'rish uchun Nested serializerdan foydalanmiz


* views.py

```
from rest_framework.viewsets import ModelViewSet
from .serializer import AdsSerializer
from .models import Ads


class AdsViewSet(ModelViewSet):
  serializer_class=AdsSerializer
  ueryset=Ads.objects.all()
```

### urls.py fayliga viewsni qo'shamiz 
esltama base urlga appning ichidagi urlni qo'shishni unitmang !!

* app/urls.py
```
from django.urls import path
from .views import AdsViewSet

urlpatterns = [
    path('category/',AdsViewSet.as_view({'get':'list'}))
]
```

ishlating
```
python manage.py runserver
```


### NATIJA


<p align="center">

<img src="https://github.com/fayzullohblog/test/blob/main/media/nested/Screenshot%20from%202023-12-06%2020-29-11.png" alt="Some programming languages logos">

</p>



  
     




























  

  
