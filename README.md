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
* Activate: `source ./<name_of_virtualenv>/bin/activate`d
* Check which python is active: `which python `
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
7. Now arrange folders as list below. 
------------------------------------------------------------------------------------
##### The updated project directory should look like this:
* Website-Project 
    * <MathMeUp_website>
        * _init_py
        * asgi.py
        * settings.py
        * urls.py
        * wsgi.py
    * requirements
    * manange.py

------------------------------------------------------------------------------------
##### How to run website on local server
* `python manage.py runserver `
##### Create Makefile file:
A makefile is a special file, containing shell commands, that you create and name makefile (or Makefile depending upon the system). ... A makefile that works well in one shell may not execute properly in another shell
* `touch Makefile`
* Example code to run server with python for Makefile: 
   ```Runserver:
        python manage.py runserver <hostname, example 0.0.0.0:80>```
* Now go to terminal and start the server with the command: `Make Runserver`
##### Hide your SECRET_KEY:
  


##### Create basic folder and files for templating
* Create a folder with named apps in MathMeup_wesbite directory: `Mkdir apps'
* Create another folder with named templates in MathMeup_wesbite directory: `mkdir templates'
    * In templates create the following files: `touch about.html`,`touch base.html`,`touch contact.html`,`touch footer.html`,`touch index.html`,`touch navbar.html`

##### How to create App:
* `mkdir apps` 
* Cd into apps directory and create three folder: `mkdir public`, `mkdir accounts`, `mkdir contact` and a file with name: __init__.py.
* Run this commad to create a app named public: `python3 manage.py startapp public <path to public folder>`
* Run this commad to create a app named accounts: `python3 manage.py startapp accounts <path to accounts folder>`
* Run this commad to create a app named contact: `python3 manage.py startapp public <path to accounts folder>`
##### The updated project directory should look like this:
```bash
 Website-Project 
    |-- <MathMeUp_website>
    |    |-- apps
    |    |-- public 
    |    |-- accounts 
    |    |-- contact
    |    | templates
    |       |-- about.html, base.html, footer.html, index,html, navbar.html
    |    |-- _init_py
    |    |-- asgi.py
    |    |-- settings.py
    |    |-- urls.py
    |    |-- wsgi.py
    |-- requirements
    |    |-- prod.txt
    |    |-- dev.txt
    |-- MathMeUp-env
    |-- manange.py
```
##### What are Routes and how to configure.  


##### Static front: 

##### Confifure Accounts page 
##### Data migration
##### Developy the your website. 
##### 