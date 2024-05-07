## Ex.05 Design a Website for Server Side Processing
## Date: 5.04.2024

## AIM:
To design a website to find surface area of a Right Cylinder in server side.

# FORMULA:

![image](https://github.com/niranjanadevi-s/MathServer/assets/141748873/7d5cb0fc-1280-4c34-9645-2251d2a94f0f)

Surface Area = 2Πrh + 2Πr<sup>2</sup>
<br>r --> Radius of Right Cylinder
<br>h --> Height of Right Cylinder

## DESIGN STEPS:

Step 1:  Clone the repository from GitHub.
Step 2:  Create Django Admin project.
Step 3:  Create a New App under the Django Admin project.
Step 4:  Create python programs for views and urls to perform server side processing.
Step 5:  Create a HTML file to implement form based input and output.
Step 6:  Publish the website in the given URL.

## PROGRAM :

# math.html
~~~
<html>
<head>
    <meta charset='utf-8'>
    <meta http-equiv='X-UA-Compatible' content='IE=edge'>
    <title>Area of Square Prism</title>
    <meta name='viewport' content='width=device-width, initial-scale=1'>
    <style type="text/css">
        body {
            background-color: red;
        }
        .edge {
            width: 1440px;
            margin-left: auto;
            margin-right: auto;
            padding-top: 250px;
            padding-left: 300px;
        }
        .box {
            display: block;
            border: Thick dashed lime;
            width: 500px;
            min-height: 300px;
            font-size: 20px;
            background-color: blue;
        }
        formelt {
            color: orange;
            text-align: center;
            margin-top: 7px;
            margin-bottom: 6px;
        }
        h1 {
            color: rgb(255, 0, 179);
            text-align: center;
            padding-top: 20px;
        }
    </style>
</head>
<body>
    <div class="edge">
        <div class="box">
            <h1>Area of a Square Prism</h1>
            <form method="POST">
                {% csrf_token %}
                <div class="formelt">
                    Side : <input type="text" name="length" value="{{l}}"></input>(in m)<br />
                </div>
                <div class="formelt">
                    Height : <input type="text" name="breadth" value="{{b}}"></input>(in m)<br />
                </div>
                <div class="formelt">
                    <input type="submit" value="Calculate"></input><br />
                </div>
                <div class="formelt">
                    Area : <input type="text" name="area" value="{{area}}"></input>m<sup>2</sup><br />
                </div>
            </form>
        </div>
    </div>
</body>
</html>
~~~
# views.py
~~~
from django.shortcuts import render
def rectarea(request):
    context={}
    context['area'] = "0"
    context['l'] = "0"
    context['b'] = "0"
    if request.method == 'POST':
        print("POST method is used")
        l = request.POST.get('length','0')
        b = request.POST.get('breadth','0')
        print('request=',request)
        print('Length=',l)
        print('Breadth=',b)
        area = 2*(int(l)**2) + 4*int(l)*int(b)
        context['area'] = area
        context['l'] = l
        context['b'] = b
        print('Area=',area)
    return render(request,'mathserverapp/math.html',context)

from django.shortcuts import render
def rectarea(request):
    context={}
    context['area'] = "0"
    context['l'] = "0"
    context['b'] = "0"
    if request.method == 'POST':
        print("POST method is used")
        l = request.POST.get('length','0')
        b = request.POST.get('breadth','0')
        print('request=',request)
        print('Length=',l)
        print('Breadth=',b)
        area = 2*(int(l)**2) + 4*int(l)*int(b)
        context['area'] = area
        context['l'] = l
        context['b'] = b
        print('Area=',area)
    return render(request,'mathserverapp/math.html',context)
~~~
# urls.py
~~~
"""
URL configuration for mathserver project.

The `urlpatterns` list routes URLs to views. For more information please see:
    https://docs.djangoproject.com/en/4.2/topics/http/urls/
Examples:
Function views
    1. Add an import:  from my_app import views
    2. Add a URL to urlpatterns:  path('', views.home, name='home')
Class-based views
    1. Add an import:  from other_app.views import Home
    2. Add a URL to urlpatterns:  path('', Home.as_view(), name='home')
Including another URLconf
    1. Import the include() function: from django.urls import include, path
    2. Add a URL to urlpatterns:  path('blog/', include('blog.urls'))
"""
from django.contrib import admin
from django.urls import path
from mathserverapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('areaofrectangle/',views.rectarea,name="areaofrectangle"),
    path('',views.rectarea,name="areaofrectangleroot")
]
~~~

## SERVER SIDE PROCESSING:

![image](https://github.com/niranjanadevi-s/MathServer/assets/141748873/b2bff026-b5d6-4f27-95d2-725e9f00388c)

## HOMEPAGE:

![image](https://github.com/niranjanadevi-s/MathServer/assets/141748873/fa8705b1-6c2c-498b-bcaa-a131fbc09fd5)

## RESULT:
The program for performing server side processing is completed successfully.
