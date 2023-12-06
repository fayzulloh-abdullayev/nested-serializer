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



<img src="https://e1.pxfuel.com/desktop-wallpaper/238/532/desktop-wallpaper-python-logo-white-silk-texture-python-emblem-programming-language-python-silk-backgrounds-with-resolution-3840x2400-high-quality-python-logo.jpg" alt="Some programming languages logos">
</p>

* npm
  ```sh
  from django.db import models

# Create your models here.



class Category(models.Model):
    title=models.CharField(max_length=50)

class Ads(models.Model):
    category=models.ForeignKey(Category,on_delete=models.CASCADE,related_name='category')
    title=models.CharField(max_length=40)
  ```
