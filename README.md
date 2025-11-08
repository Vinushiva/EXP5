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
math.html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lamp Power Calculator</title>

    <style>
        body {
            font-family: Arial, Helvetica, sans-serif;
            background: linear-gradient(135deg, #6a11cb, #2575fc);
            height: 100vh;
            margin: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            color: #fff;
        }
        .container {
            background: rgba(255, 255, 255, 0.2);
            padding: 30px;
            border-radius: 15px;
            width: 350px;
            backdrop-filter: blur(10px);
            box-shadow: 0 8px 20px rgba(0,0,0,0.2);
        }
        h2 {
            text-align: center;
            margin-bottom: 20px;
            letter-spacing: 1px;
        }
        label {
            display: block;
            margin-top: 12px;
            font-size: 15px;
            font-weight: bold;
        }
        input {
            width: 100%;
            padding: 10px;
            margin-top: 5px;
            border-radius: 8px;
            border: none;
            outline: none;
            font-size: 16px;
        }
        button {
            margin-top: 20px;
            width: 100%;
            padding: 12px;
            background: #ffcc00;
            color: #000;
            border: none;
            font-size: 18px;
            border-radius: 8px;
            cursor: pointer;
            font-weight: bold;
            transition: 0.2s;
        }
        button:hover {
            background: #ffdd33;
            transform: scale(1.03);
        }
        .result {
            margin-top: 20px;
            padding: 15px;
            background: rgba(0,0,0,0.3);
            border-radius: 10px;
            text-align: center;
            font-size: 20px;
            font-weight: bold;
        }
    </style>
</head>
<body>

    <div class="container">
        <h2>Lamp Power Calculator</h2>

        <label for="intensity">Intensity (I) in Amps:</label>
        <input type="number" id="intensity" placeholder="Enter intensity">

        <label for="resistance">Resistance (R) in Ohms:</label>
        <input type="number" id="resistance" placeholder="Enter resistance">

        <button onclick="calculatePower()">Calculate Power</button>

        <div class="result" id="result">Power: </div>
    </div>

    <script>
        function calculatePower() {
            let I = parseFloat(document.getElementById("intensity").value);
            let R = parseFloat(document.getElementById("resistance").value);
            
            if (isNaN(I) || isNaN(R)) {
                document.getElementById("result").innerHTML = "Please enter both values!";
                return;
            }

            let P = I * R;
            document.getElementById("result").innerHTML = "Power: " + P + " watts";
        }
    </script>

</body>
</html>

views.py
from django.shortcuts import render

def powerlamp(request):
    context={}
    context['Power'] = ""
    context['I'] = ""
    context['R'] = ""
    if request.method == 'POST':
        print("POST method is used")
        I = request.POST.get('Intensity','')
        R = request.POST.get('Resistence','')
        print('request=',request)
        print('Intensity=',I)
        print('Resistence=',R)
        Power = int(I) * int(I) * int(R)
        context['Power'] = Power
        context['I'] = I
        context['R'] = R
        print('Power=',Power)
    return render(request,'mathapp/math.html',context)

urls.py

from django.contrib import admin
from django.urls import path
from mathapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('math.html', views.powerlamp, name='powerlamp'),
]
```



## SERVER SIDE PROCESSING:
![alt text](<Screenshot 2025-11-08 212204.png>)
![alt text](<Screenshot 2025-11-08 212230.png>)
![alt text](<Screenshot 2025-11-08 212251.png>)



## HOMEPAGE:
![alt text](<Screenshot 2025-11-08 205520.png>)


## RESULT:
The program for performing server side processing is completed successfully.
