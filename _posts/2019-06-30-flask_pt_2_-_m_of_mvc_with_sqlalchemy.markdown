---
layout: post
title:      "Flask pt.2 - M of MVC with SQLAlchemy"
date:       2019-06-30 23:49:21 +0000
permalink:  flask_pt_2_-_m_of_mvc_with_sqlalchemy
---


Of course it’s probably a good idea to read and work through a tutorial in order, as the creator intended, but I didn’t do that.

Continuing with my Flask app form my last post, when I create a new project I usually have an idea of models I will be using and set up the database immediately after creating the app. So to satisfy my curiosity, I skipped reading most of part 3 of the tutorial covering configuration keys and forms using flask-wtf. (`pip3 install flask-wtf`)

I wanted to go over database set up, which is covered in [part 4](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-iv-database). Then in consideration of an MVC framework, after this section I will have learned basic views and models. Basic controller actions are actually covered in part 3 of the tutorial as handling form submissions.

As I mentioned in my previous post, Flask doesn't have a preset ORM or database, so you must choose and install your own.

* `pip3 install flask-sqlalchemy` - an ORM (like Ruby ActiveRecord) used with flask, supports sql, postgres, mysql, etc.
* `pip3 install flask-migrate` - an extension that is a flask wrapper for Alembic, sqlalchemy’s db migration framework.

After installing these two extensions, changes will be made in `config.py` (set up in skipped 3rd chapter) to allow configure database usage in the app. In this file, the database used is also specified. (sqlite in the blog example)

In `__init__.py` the app will then import the flask-sqlalchemy and flask-migrate modules, and create instances of each to be used.

In a new file, `app/models.db` , the SQLAlchemy database is imported and used to create models using `from app import db` . The schema is similar to what we are used to using with ActiveRecord (it is still using sqlite) but the syntax is different.  The extra arguments for each column specify that the field must be unique and indexed and a `__repr__` method is used inside the class to tell Python how to print the object.

Multiple models can be included in the `app/models.py` file, and extra attributes like foreign keys and default values can also be added as comma-separated extra arguments of `db.Column` For example, db.ForeignKey('user.id') and default=datetime.utcnow (need to import datetime)

```
from app import db

class User(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    username = db.Column(db.String(64), index=True, unique=True)

    def __repr__(self):
        return '<User {}>'.format(self.username)
```

Migrations are handled with a migration repository, similarly to ActiveRecord migrations. The `flask db` command is added by flask-migrate.

Run `flask db init` to create migration repo structure in your project.

Flask can automatically generate migrations by comparing the models defined in `app/models.py` to the actual database schema using `flask db migrate -m ‘users-table’` The `-m` flag is for a migration description.

SQLAlchemy uses snake case naming convention for its tables. So for a table may be named, `address_and_phone_number`. The `__tablename__` attribute in a model class can be used to customize the name.

The generated migration (in `migrations/versions/`) has upgrade() and downgrade() functions to add and remove the changes to the database. Run `flask db upgrade` to change the database.

Use `flask db downgrade` to remove the last migration.

**After setting up the database, below are some ways to interact with your app’s database in the terminal.**

After opening python3 in your terminal and importing your app (be in right directory) you can create instances of the models you defined and access and change the database using `db.session` . You can also query models using the class methods in a `User.query` like structure. The full [SQLAlchemy](https://flask-sqlalchemy.palletsprojects.com/en/2.x/) docs show all the command options

```
python3
from app import db
from app.models import User, Post
u = User(username='john', email='john@example.com')
db.session.add(u)
db.session.commit()
User.query.all()
```

You can also just run `flask shell` in the terminal to open an interpreter in the context of the application. It pre-imports the app so you can interact with it, and you can configure it in `my-app-name.py` to have the database models available as well.

```
from app import app, db
from app.models import User, Post

@app.shell_context_processor
def make_shell_context():
    return {'db': db, 'User': User, 'Post': Post}
```

[Link](https://github.com/jk-me/pytodo) to my github repo for this project. (Check out earlier commits to see the process described above.)
