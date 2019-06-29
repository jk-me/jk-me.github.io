---
layout: post
title:      "Trying out new frameworks - Flask"
date:       2019-06-29 05:12:41 +0000
permalink:  trying_out_new_frameworks_-_flask
---

I wanted to try out some other web frameworks in different languages to see how they worked and if I would have a preference for one. The first new one I tried was Python Flask.

I had learned Python a few years ago in college and wanted to refresh my knowledge of the language, and learning a popular web deveopment framework like Flask seemed like a good way to do so. Flask, compared to Django, is much simpler, without many preset packages and add-ons. It allows you to choose what you need, and avoid unnecessary package bloat for smaller projects. While flexible and easy to use for small projects, Flask also scales well and is used for sites like Reddit, Netflix, Airbnb and Lyft, among others.

**Flask Setup**

I followed Miguel Grinberg's Flask Mega Tutorial [link](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-i-hello-world ), which explains each step in much better detail and what tools you are using/what the purpose of each step is, but I will go over the steps to provide a brief overview of how a Flask app is created and how it is different/similar to Sinatra and Ruby on Rails.

You will:
* Install python3 if you don’t have it -> `brew install python3`
* Create a `venv` virtual environment to separate your project’s dependencies from your operating system and other projects `python -m venv myvenv`
* Activate your virtual environment `source venv/bin/activate`  (Deactivate with `deactivate` in terminal)
* *Be sure to have your venv activated when installing packages, or it will also be added to your entire system*
* Install Flask using pip, python’s package installer
* Copy the code and file structure outlined to create a simple ‘hello world’ python server
* *Includes a top level file my-app-name.py that imports instance of Flask app*


Currently homebrew-installed python3 includes pip3, which runs with `pip3` alias instead of just pip - so you would need to run `pip3 install Flask`. You may need to run `brew postinstall python3` to install pip

Using the file structure outlined in Grinberg’s tutorial, start your server by setting the flask environment variable `export FLASK_APP=my-app-name.py` After setting the environment variable you can run `flask run` and navigate to `localhost:5000`

You will need to reload the development server each time you make changes, like in Sinatra.

You will have to set flask env var for each new terminal session unless you use an environment variable
Install `pip3 install python-dotenv` , then in the `.flaskenv` file in root, add the variable as `FLASK_APP=my-app-name.py`

Flask doesn’t have preset ORM (Object Relational Mapper, or database manager) like Rails ActiveRecord. SQLAlchemy is a python library ORM often used with Flask. It can be used with SQLite, postgreSQL, MySQL and other database engines. Another combination commonly used is MongoEngine or MongoKit with MongoDB.

So far, the routes and the view layouts are both located in the `app/routes.py` file. To separate concerns, make templates in app/templates, for example `app/templates/index.html` This will be structured like a regular html file, but with inserted variables written with double brackets, for ex {% raw %}`{{user.username}}`.{% endraw %}

```
#in my-app-name/app/routes.py

from flask import render_template
from app import app

@app.route('/')
@app.route('/index')

def index():
    user = {'username': 'Jenny'}
    return render_template('index.html', title='Home', user=user)
```

The routes.py file then changes to include `from flask import render_template` to import the rendering tool. The user in the index function is a temporary data object to view in the server since there is no database yet.

Control logic can also be used in the html templates. Flask imports render_template, which uses the Jinja2 template engine to render, and it uses marker tags to wrap keywords for control statements, very similarly to using erb tags in Ruby.
{% raw %}
```
Flask:
{% ... %}    //logic keywords
{{ ... }}    //display value

 Ruby:
 <% ... %>     //logic keywords
 <%= ... %>   //display value
```
{% endraw %}

Python syntax uses `if … elif … else` and `for .. in ...` keywords and Flask also requires the `endif` and `endfor` keywords to mark the end of the statement.

Templates can also be inherited in Flask, like as in other frameworks, such as for a navigation bar. For a `base.html` file also in the templates directory, containing a navbar to be inherited, {%raw%}`{% block UniqueName%} {% endblock%}`{%endraw%} signals where another template can be inserted.

This block statement must also wrap around the content in the derived template file, with the same UniqueName as in the extended template. `extends base.html` is included at the top of the file to inherit the other template.

[Link](https://github.com/jk-me/pytodo) to my GitHub repo for this project.
