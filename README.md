# Ex.05 Design a Website for Server Side Processing
## Date:

## AIM:
 To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side. 


## FORMULA:
P = I<sup>2</sup>R
<br> P --> Power (in watts)
<br> I --> Intensity
<br> R --> Resistance

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
html

<html>
<head>
<title>Power Calculator</title>
<h1 style="color:purple">
    POWER OF LAMP FILAMENT
</h1>
<style type="text/css">
body {
    background-color: blue;
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
    border: grey;
    width: 1000px;
    min-height: 300px;
    font-size: 20px; 
    background-color: red;
}
.formelt { 
    color: cyan; 
    text-align: center; 
    margin-top: 7px; 
    margin-bottom: 6px;
}
h1 {
    color: skyblue;
    text-align: center;
    padding-top: 20px;
}    
</style>
</head>
<body>
    <div class="edge">
    <div class="box">
    <h1>Power Calculator</h1>
    <form method="POST">
    {% csrf_token %}
    <div class="formelt">
        Current (I): <input type="text" name="Current" value="{{I}}"></input> (in Amperes)<br/>
    </div>
    <div class="formelt">
        Resistance (R): <input type="text" name="Resistance" value="{{R}}"></input> (in Ohms)<br/>
    </div>
    <div class="formelt">
        <input type="submit" value="Calculate"></input><br/>
    </div>
    <div class="formelt">
        Power (P): <input type="text" name="Power" value="{{P}}"></input> (in Watts)<br/>
    </div>
    </form>
    </div>
    </div>
</body>
</html>
urls
from django.contrib import admin
from django.urls import path
from myapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('power/', views.power, name="power"),
    path('', views.power, name="powerroot")
]
view
from django.shortcuts import render

def power(request):
    context = {'P': "0", 'I': "0", 'R': "0"}
    if request.method == 'POST':
        print("POST method is used")
        I = request.POST.get('Current', '0')
        R = request.POST.get('Resistance', '0')
        print('Current =', I)
        print('Resistance =', R)
        try:
            I_val = float(I)
            R_val = float(R)
            P = I_val * I_val * R_val   # Formula: P = I² * R
            context['P'] = round(P, 2)
            context['I'] = I
            context['R'] = R
            print('Power =', P)
        except ValueError:
            context['P'] = "Invalid Input"
    return render(request, 'myapp/power.html', context)

    ```

## SERVER SIDE PROCESSING:
<img width="1335" height="755" alt="Screenshot 2025-12-27 002415" src="https://github.com/user-attachments/assets/8a61eae1-f7a5-42a5-9c2a-b4a40054893b" />

## HOMEPAGE:
![im](https://github.com/user-attachments/assets/246da9c6-774b-4073-8c1c-c7f580d538ce)

## RESULT:
The program for performing server side processing is completed successfully.
