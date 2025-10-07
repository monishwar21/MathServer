# Ex.05 Design a Website for Server Side Processing
## Date:5/10/2025

## AIM:
 To design a website to calculate the Body Mass Index (BMI) in the server side


## FORMULA:
BMI = W/H2
BMI-->Body Mass Index
w-->weight
h-->Height

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM :
```
math.html

<html>
    <head>
        <title>BMI_Calculator</title>
        <style>
            body {
                background-color:rgb(255, 42, 0);
                font-family: Arial;
                display: flex;
                justify-content: center;
                align-content: center;
                height: 150vh;
            }
            .bmibox {
                background-color: rgb(199, 241, 10);
                border: 5px inset rgb(32, 14, 123);
                padding: 30px;
                text-align: center;
                height: 350px;
                width: 500px;
                display: block;
            }
            input[type="text"] {
                width: 80%;
                padding: 12px;
                margin: 15pypx;
                border: 3px solid black;
                background-color: rgb(236, 125, 167);
            }
        </style>
    </head>

    <body>
        
        <br>
        <div class="bmibox">
            <h2 align="center">BMI-CALCULATOR  <br> <br> K MONISHWAR (25014914)</h2> <br>
            <form method="POST">
            {%csrf_token %}
            <div class="formelt">
            Height: <input type="text" name="height" value="{{height}}" placeholder="Enter height in m">
            <br>
            <br>
            </div>
            <div class="formelt">
            Weight: <input type="text" name="weight" value="{{weight}}" placeholder="Enter weight in kg">
            <br>
            <br>
            </div>
            <div class="formelt">
            <input  type="submit" value="Calculate">
            <br>
            <br>
            </div>
            <div class="formelt">
            BMI: <input type="text" name="BMI" value="{{BMI}}">
            <br>
            </div>
            </form>
        </div>
    </body>
</html>

views.py

from django.shortcuts import render
def calculate_BMI(request):
  context = {}
  context['BMI'] = "0"
  context['height'] = "0"
  context['weight'] = "0"
  if (request.method=="POST"):
    print("POST method is used")
    height = request.POST.get("height","0")
    weight = request.POST.get("weight","0")
    print("Request=", request)
    print("Height=", height)
    print("Weight=", weight)
    BMI = float(weight)/(float(height)*float(height))
    context['BMI'] = BMI
    context['height'] = height
    context['weight'] = weight
    print("BMI=", BMI)
  return render (request,'mathapp/math.html',context)

  urls.py

  from django.contrib import admin
from django.urls import path
from mathapp import views
urlpatterns = [
    path("admin/", admin.site.urls),
    path('calculate_BMI/', views.calculate_BMI, name = "BMI"),
    path('', views.calculate_BMI, name="BMIroot")
]
```

## SERVER SIDE PROCESSING:

![alt text](<Screenshot (46).png>)
## HOMEPAGE:

![alt text](<Screenshot (45).png>)

## RESULT:
The program for performing server side processing is completed successfully.
