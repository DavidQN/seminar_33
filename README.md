# Deployment with Heroku

Steps to deploy your first Flask application on Heroku.

## What you need beforehand

-   Git
-   Heroku Account
-   Heroku CLI (https://devcenter.heroku.com/articles/heroku-cli)

### Deploying a local Flask application

First let us create a folder to contain our application and let us call it `herokuFlask`

```shell
$ mkdir herokuFlask
```

After we have created our folder let us enter that folder

```shell
$ cd herokuFlask
```

Now let us create our Flask application and call our application `application.py`

```
touch application.py
```

Within `application.py` let us return 'Hello World!'.

```python
from flask import Flask

app = Flask(__name__)

@app.route('/')
def hello():
    return 'Hello, World!'
```

##### If you are following these instructions on your local machine and not the CS50 IDE then don't forget to setup your `virtualenv` if you use one and to `pip install flask`.

Now let us export our Flask application

```shell
export FLASK_APP=application.py
```

And now run this application locally

```shell
flask run
```

Great we should get

<img width="303" alt="screen shot 2018-07-30 at 3 07 00 pm" src="https://user-images.githubusercontent.com/23644019/43417921-65979b8e-940a-11e8-92eb-30829c84f000.png">

OKAY! Now let us actually deploy this Flask application to heroku.

###### If you have not already setup a Heroku account, please do so since you cannot continue without it.

---

### Deploying a Flask application to Heroku

Let us install `Gunicorn`

```
pip install gunicorn
```

Let us create our Procfile

```
touch Procfile
```

Within the Procfile

```
web gunicorn application:app
```

Now let us create our Heroku application (this should generate a heroku app for us)

```
heroku create
```

Now let us open the heroku application

```
heroku open
```

We should just get a generic page that looks similar to this
<img width="538" alt="screen shot 2018-07-31 at 1 48 12 am" src="https://user-images.githubusercontent.com/23644019/43440060-dc4a8076-9463-11e8-8784-d44a0d92e53c.png">

Place our pip installs to a `requirements.txt` file

```
pip freeze > requirements.txt
```

Put everything to our local repository

```
git init
git add .
git commit -m "Deploy to heroku"
```

Now let us push our code to the Heroku applications remote git repo

```
git push heroku master
```

Now if you want to see your application, when you run `heroku open` you should be able to see your application now

```
heroku open
```

---
