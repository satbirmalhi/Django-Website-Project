## Django-Website-Project 
> Math is hard, so is life!
> Django is a high-level Python web framework that encourages rapid development and clean, pragmatic design. Built by    
  experienced developers, it takes care of much of the hassle of web development, so you can focus on writing your app without needing to reinvent the wheel. It’s free and open source. 
## How to write README.md: Using Markdow Cheat: [Cheatme](https://www.markdownguide.org/cheat-sheet/)
------------------------------------------------------------------------------------------------------

## The Collaboration Setup for the project
-----------------------------------------------------------------------------------------------------
* Setup Brew: [Brew](https://brew.sh/)
* Setup oh my zsh: [Zsh](https://www.freecodecamp.org/news/how-to-configure-your-macos-terminal-with-zsh-like-a-pro-c0ab3f3c1156/)
* Setup git and github:[git](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup)
    * git [cheatsheet](https://education.github.com/git-cheat-sheet-education.pdf)

----------------------------------------------------------------------------------
### [Install Virtual Environment](https://virtualenv.pypa.io/en/latest/installation.html)
* Install:  brew and update it
* `pip3  install virtualenv`
* Check all the package in your global machine: `pip3 list` 
* Check: `virtualenv --version` 
* `virtualenv -p python3.9 <name_of_virtualenv>`
* Activate: `source ./<name_of_virtualenv>/bin/activate`
* Check which python is active: `which python `
* Create a gitignore file and copy paste <name_of_virtualenv> in it: `touch .gitignore` `echo "<name_of_virtualenv>" .gitignore`
* Deactivate when switch to another the application: `deactivate`
----------------------------------------------------------------------------------
### [Django homepage](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/skeleton_website#overview)
#### Task 1: Creating Django Project
1. Create a folder requirements, then create prod.txt and dev.txt
    * `mkdir requirements`
    * `cd requirements`
    * `touch prod.txt` and `touch dev.txt`
    
2. Install Django: `pip install Django`
3. Copy local packages to prod.txt: `pip freeze --local > prod.txt`
4. Copy all the prod requirements to dev.txt: `echo '-r prod.txt' > dev.txt`
5. Check: `cat prod.txt` and `cat dev.txt`
6. Create Dajango project: `djando-admin startproject {Website_name}` . Make sure to run this command in your website folder:

------------------------------------------------------------------------------------
##### Now arrange folders as list below. 
  ```zsh
  Website-Project
    |-- <MathMeUp_website>
    |       |--_init_py
    |       |-- asgi.py
    |       |-- settings.py
    |       |-- urls.py
    |       |--wsgi.py
    |-- <MathMeUp-env>
    |-- requirements
            |-- prod.txt
            |-- dev.txt
    |--.gitignore
    |-- manange.py
    |-- READEME.md
```

------------------------------------------------------------------------------------
##### How to run website on local server
* `python manage.py runserver `
    * this command has created a data base with the name db.sqlite3. Copy the name of this data base in .gitignore file. 
##### Create Makefile file:
A makefile is a special file, containing shell commands, that you create and name makefile (or Makefile depending upon the system). ... A makefile that works well in one shell may not execute properly in another shell
* `touch Makefile`
* Example code to run server with python for Makefile: 
   ```Runserver:
        python manage.py runserver <hostname, example 0.0.0.0:80>```
* Now go to terminal and start the server with the command: `Make Runserver`
##### Hide your SECRET_KEY:
1. Install python-decouple to create a local project environment to store your secret key.
    ```pip install python-decouple```
2. Create a .env file in your base directory (where manage.py is).

 ```zsh
  Website-Project
    |-- <MathMeUp_website>
    |   |--_init_py
    |   |-- asgi.py
    |   |-- settings.py
    |   |-- urls.py
    |   |--wsgi.py
    |-- <MathMeUp-env>
    |-- requirements
    |-- db.sqlite3
    |-- .env
    |--.gitignore
    |--manange.py
    |-- README.md
```
3. Add .env to your .gitignore file.
``` open your .gitignore and type in .env```
4. Add your SECRET_KEY from your settings.py file into the .env file like so (without quotes)
```
**Inside of your .env file** 
SECRET_KEY=qolwvjicds5p53gvojw&a^&c4&16ou7 # <- Example key, SECRET_KEY=yoursecretkey
```
5. Inside of your settings.py file, add the following settings:
```
from decouple import config
SECRET_KEY = config('SECRET_KEY')
```
6. Check if all is working fine: `Make runserver`


  
##### Create basic folder and files for templating
* Create a folder with name apps in MathMeup_wesbite directory: `Mkdir apps`
* Create another folder with name templates in MathMeup_wesbite directory: `mkdir templates`
    * In templates folder create the following files: `touch about.html`,`touch base.html`,`touch contact.html`,`touch footer.html`,`touch index.html`,`touch navbar.html`

##### How to create App:
* cd into apps directory and create three folder: `mkdir public`, `mkdir accounts`, `mkdir contact` and a file with name:`touch __init__.py`.
*  Go back to your base directory (where manage.py is).
* Run this command to create a app named public: `python3 manage.py startapp public <path to public folder>`
* Run this command to create a app named accounts: `python3 manage.py startapp accounts <path to accounts folder>`
* Run this command to create a app named contact: `python3 manage.py startapp contact <path to accounts folder>`
##### The updated project directory should look like this:
```zsh
 Website-Project 
    |-- <MathMeUp_website>
    |    |-- apps
    |        |-- public 
             |  |- migrations, __init__,admin.py,apps.py,models.py,tests.py,views.py
    |        |-- accounts 
             |  |-- migrations, __init__,admin.py,apps.py,models.py,tests.py,views.py,
    |        |-- contact
             |  |--|migrations, __init__,admin.py,apps.py,models.py,tests.py,views.py,
    |    |-- templates
    |       |-- about.html, base.html, contact.html footer.html, index,html, navbar.html
    |    |-- _init_py
    |    |-- asgi.py
    |    |-- settings.py
    |    |-- urls.py
    |    |-- wsgi.py
    |-- <MathMeUP-env>
    |-- requirements
    |    |-- prod.txt
    |    |-- dev.txt
    |--.gitignore
    |-- db.sqlite3
    |--.env
    |-- Makefile
    |-- manange.py
    |-- README.md
```
##### What are Routes and how to configure.  
1. In Settings.py add the following setting: 
    *  Setting the project directory path. Write this below Base Dir
```
import os
PROJECT_DIR = os.path.join(BASE_DIR, "<MathMeUp_website>")
```
    * Go into settings.py file and then inside  Templates replace "DIRS" with the follwing codes:
        ```"DIRS": [os.path.join(PROJECT_DIR, "templates")],```
2. In the urls.py (of the base folder) paste the following codes:  
```
from django.contrib import admin
from django.urls import path, include
from django.contrib.auth import views as auth_views
urlpatterns = [
    path("admin/", admin.site.urls),
    path("", include("MathMeUp_website.apps.public.urls")),
    ]
```
2. Go to apps folder and then public app. There creare a file named urls.y and paste the following codes:

```
from django.urls import path
from . import views
    
app_name = "public"
urlpatterns = [
    path("", views.index, name="index"),
    path("about", views.about, name="about"),
    
        ]
```
3. Now open views.py of public app and paste the following code

```
from django.http import HttpResponse, HttpRequest
from django.shortcuts import render

def index(request: HttpRequest) -> HttpResponse:
        return render(request, "index.html")
def about(request: HttpRequest) -> HttpResponse:
        return render(request, "about.html")
```




##### [Static front using BootStrap](): 
1. Go to [bootstrap freelance website](https://startbootstrap.com/theme/freelancer) and download freelance website design 
2. Create a folder with name static(in base directory where manage.py file is)
3. Create a another folder inside of static with name theme 
4. Copy and paste all the file from your freelance folder (which you just downloaded from bootstrap website) into theme folder 
5. Go into settings.py file and configure the following path below static_url
```
STATICFILES_DIRS = [os.path.join(BASE_DIR,"static")]
```
6. Attachihng index, base, nav, and footer 
    * index.html
    ```
    {% extends "base.html" %}
    {% block title %} 
    Home Page  
    {% endblock %}

    {% block content %}
    This is boday 
    {% endblock %}

    ```
    * base.html
    ```
    {% load static %}
    
    <head>
        {% block title %}   {% endblock %}
    </head>

    <body>
    {% include 'navbar.html'%}
    <main id="main">
    {% block content%}   {% endblock %}
    </main>
    {% include 'footer.html'%}
    </body>
    </html>
    ```
7. Next we will copy and past code from freelancer theme to our main html files. Follows the next steps on this [video]()
    * Copy the following codes from index.htm (of static folder) and past into base.html (of templates folder)
    
    ```
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no" />
        <meta name="description" content="" />
        <meta name="author" content="" />
        <title>Freelancer - Start Bootstrap Theme</title>
        <!-- Favicon-->
        <link rel="icon" type="image/x-icon" href="assets/favicon.ico" />
        <!-- Font Awesome icons (free version)-->
        <script src="https://use.fontawesome.com/releases/v5.15.3/js/all.js" crossorigin="anonymous"></script>
        <!-- Google fonts-->
        <link href="https://fonts.googleapis.com/css?family=Montserrat:400,700" rel="stylesheet" type="text/css" />
        <link href="https://fonts.googleapis.com/css?family=Lato:400,700,400italic,700italic" rel="stylesheet" type="text/css" />
        <!-- Core theme CSS (includes Bootstrap)-->
        <link href="css/styles.css" rel="stylesheet" />
        </head>
    ```
     * update the followind code 
        * add: `{% load static %}`
        * change: `<link href="css/styles.css"` into `<link href="{% static "theme/css/styles.css"%}"`
        * delete: ` <!-- Favicon--> <link rel="icon" type="image/x-icon" href="assets/favicon.ico" />`
     * copy the following codes from index.htm of static folder and paste into base.html

    ```
    <!-- Bootstrap core JS-->
        <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.0/dist/js/bootstrap.bundle.min.js"></script>
        <!-- Core theme JS-->
        <script src="js/scripts.js"></script>
        <!-- * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *-->
        <!-- * *                               SB Forms JS                               * *-->
        <!-- * * Activate your form at https://startbootstrap.com/solution/contact-forms * *-->
        <!-- * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *-->
        <script src="https://cdn.startbootstrap.com/sb-forms-latest.js"></script>
    ```
     * Change: `<script src="js/scripts.js"></script>` into `<script src="{% static "theme/js/scripts.js" %}"></script>`
8. Inspect the page and make sure all the files loaded properly 
9. ### Navbar 
    * copy and paste the code from index.html into navbar.html and update the required changes as mentioned in the video. 
    ```
    <!-- Navigation-->
        <nav class="navbar navbar-expand-lg bg-secondary text-uppercase fixed-top" id="mainNav">
            <div class="container">
                <a class="navbar-brand" href="#page-top">Start Bootstrap</a>
                <button class="navbar-toggler text-uppercase font-weight-bold bg-primary text-white rounded" type="button" data-bs-toggle="collapse" data-bs-target="#navbarResponsive" aria-controls="navbarResponsive" aria-expanded="false" aria-label="Toggle navigation">
                    Menu
                    <i class="fas fa-bars"></i>
                </button>
                <div class="collapse navbar-collapse" id="navbarResponsive">
                    <ul class="navbar-nav ms-auto">
                        <li class="nav-item mx-0 mx-lg-1"><a class="nav-link py-3 px-0 px-lg-3 rounded" href="#portfolio">Portfolio</a></li>
                        <li class="nav-item mx-0 mx-lg-1"><a class="nav-link py-3 px-0 px-lg-3 rounded" href="#about">About</a></li>
                        <li class="nav-item mx-0 mx-lg-1"><a class="nav-link py-3 px-0 px-lg-3 rounded" href="#contact">Contact</a></li>
                    </ul>
                </div>
            </div>
        </nav>
    ```

- ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+) `#f03c15`
- ![#c5f015](https://via.placeholder.com/15/c5f015/000000?text=+) `#c5f015`
- ![#1589F0](https://via.placeholder.com/15/1589F0/000000?text=+) `#1589F0`


 



##### Confifure Accounts page 
##### Data migration
##### Developy the your website. 
##### 