# Ex.08 Design of Interactive Image Gallery
## Date:

## AIM:
To design a web application for an inteactive image gallery with minimum five images.

## DESIGN STEPS:

### Step 1:
Clone the github repository and create Django admin interface.

### Step 2:
Change settings.py file to allow request from all hosts.

### Step 3:
Use CSS for positioning and styling.

### Step 4:
Write JavaScript program for implementing interactivity.

### Step 5:
Validate the HTML and CSS code.

### Step 6:
Publish the website in the given URL.

## PROGRAM :
```
. Create URL routing
photogallery/urls.py
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('gallery.urls')),  # Route root to gallery app
]
gallery/urls.py
Create a new file urls.py in the gallery app:
from django.urls import path
from . import views

urlpatterns = [
    path('', views.gallery_view, name='gallery'),
]

4. Create the view
gallery/views.py
from django.shortcuts import render

def gallery_view(request):
    images = [
        'image1.jpg',
        'image2.jpg',
        'image3.jpg',
        'image4.jpg',
        'image5.jpg',
    ]
    return render(request, 'gallery/gallery.html', {'images': images})

5. Add images & static files
Create the folder structure inside your app:
gallery/
  static/
    gallery/
      images/
        image1.jpg
        image2.jpg
        image3.jpg
        image4.jpg
        image5.jpg
Place your 5 images here (use any photos you like).

6. Create the HTML template
Create gallery/templates/gallery/gallery.html:
{% load static %}
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Interactive Photo Gallery</title>
  <style>
    .gallery img {
      width: 200px;
      margin: 10px;
      cursor: pointer;
      transition: transform 0.3s;
      border-radius: 8px;
      box-shadow: 0 2px 5px rgba(0,0,0,0.3);
    }
    .gallery img:hover {
      transform: scale(1.1);
    }
    #lightbox {
      position: fixed;
      top:0; left:0; right:0; bottom:0;
      background: rgba(0,0,0,0.8);
      display:none;
      justify-content:center;
      align-items:center;
      z-index: 999;
    }
    #lightbox img {
      max-width: 90%;
      max-height: 90%;
      border-radius: 10px;
      box-shadow: 0 0 15px white;
    }
  </style>
</head>
<body>

<h1>Interactive Photo Gallery</h1>
<div class="gallery">
  {% for img in images %}
    <img src="{% static 'gallery/images/'|add:img %}" alt="Photo" onclick="openLightbox(this.src)">
  {% endfor %}
</div>

<div id="lightbox" onclick="closeLightbox()">
  <img id="lightbox-img" src="" alt="Large view">
</div>

<script>
  function openLightbox(src) {
    document.getElementById('lightbox-img').src = src;
    document.getElementById('lightbox').style.display = 'flex';
  }
  function closeLightbox() {
    document.getElementById('lightbox').style.display = 'none';
  }
</script>

</body>
</html>

```
## OUTPUT:
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/ced2f789-7c53-4167-9572-79b63c8e57aa" />

## RESULT:
The program for designing an interactive image gallery using HTML, CSS and JavaScript is executed successfully.
