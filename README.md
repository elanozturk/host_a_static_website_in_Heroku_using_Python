


# Host a static website in Heroku for FREE using Python Flask framework

# Guideline:


## Part 1: Push your website live to Heroku

### 1.Follow [Heroku Documention](https://devcenter.heroku.com/articles/getting-started-with-python)

    -Download [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
    -Download [Heroku CLI](https://devcenter.heroku.com/articles/getting-started-with-python#set-up) (Command Line Interface)


### 2.Create a [Heroku account](https://signup.heroku.com/)


### 3.Create a project folder and organize the folder structure - in your Terminal / Command Line Prompt

$mkdir Website_Example

$cd Website_Example

$mkdir templates

so your folder structure will look like:

**Website_Example**

>**templates**
>> index.html

### 4.Create a virtual environment and activate it

**$pip install virtualenv**

make a virtualenv called "venv":

**$virtualenv venv**

activate this virtual env:

    - macOS:

        $source venv\bin\activate

    - windows:

        $venv\Scripts\activate


### 5.Init Git in project folder

    $git init


### 6.pip install all required dependencies:

    $pip install Flask

    $pip install gunicorn


### 7.Create a Flask app/backend
    $touch index.py


```python
from flask import Flask, render_template


app = Flask(__name__)


@app.route("/") #www.domain.com - render homepage
def index():

    return render_template("index.html")


if __name__ == "__main__":

    app.run(debug=False)
```

### 8.Create a Procfile

$touch Procfile

make sure you capitalize the first letter and name the file WITHOUT any extension. in your Procfile, include:

**web: gunicorn index:app**

make sure you:

1. do **NOT** include any space between "index:" and "app" - "index" is the .py file where your Flask backend lives in and "app" is the variable name of the flask object that's defined in index.py file.  

2. include **ONE** space between "web:" and "gunicorn" -


### 9.Create a requirements.txt file


$pip freeze > requirements.txt



### 10.Push our app/website to Heroku

    $heroku login
-your browser pops up asking you to log into your Heroku CLI

    $heroku create
-create a new Heroku app randomly named by Heroku (you can pass a specific App name but it has to be
uniquely available.)


    $ git status
-track your file changes and locate the untracked files detected by git

    $ git add .
-add all files to git staging area so that you can push files to Heroky in next steps

    $ git commit -m"give your wished comments for app pushing"
-this is to commit all your changes

    $ git push heroku master
-finally pushing your apps and files to Heroku server
wait a few minutes and let Heroku do all the heavy liftings for you. After successfully deploying:

    $heroku open
-open your app url and view it in your browser.


## Part 2: Add a custom domain to your Heroku hosted app

- Get a free domain


  1. Go to [freenom](https:freenom.com) to sign up an account
  2. Grab a free domain


- Visit your hosted webste in Heroku

  1. Log in Heroku and go to [dashboard](https://https://dashboard.heroku.com/apps) to visit the hosted app

  2. Add custom domains in your app's setting page.


- Add Heroku DNS CNAME records to Freenom DNS console.


  1. Head over to Freenom DNS Console

  2. Point CNMAE records to Heroku-required records


- Await a few minutes to see your website live @ yourwebsite.com
