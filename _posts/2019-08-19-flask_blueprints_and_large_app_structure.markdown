---
layout: post
title:      "Flask Blueprints and Large App Structure"
date:       2019-08-19 17:52:23 +0000
permalink:  flask_blueprints_and_large_app_structure
---

I was curious about how larger Flask applications were structured, so I checked out the section on A Better Application Structure.

Link to original tutorial: [Miguel Grinberg's Flask Mega Tutorial - part XV](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-xv-a-better-application-structure)

From the basic application structure I’ve learned so far to create the simplest Flask application, all the routes and controller actions existed in one file, all the model definitions existed in another, and all the templates existed in one directory. 

This would get unwieldy quickly, as more features and components are added to an application. I wanted to see how larger applications would be organized, as it differs greatly from how Rails generators create scaffolding. 

Large Flask apps can be organized with Blueprints. It’s an extension of flask that must be imported and initialized, and creates a structure that represents a feature of your application, for example user authentication. It would be a directory inside your app that encompass all the routes and form templates needed and then be registered as a component with your main application.

One benefit of this is that it makes code more reusable between projects. Another is that you can change all the decorators (route definers, etc.) so that they rely on the blueprint `@bp.route` instead of a global application instance `@app.route`. This comes in handy for testing, as you can then create an application factory function to create new instances of your application as needed, with controlled configurations and ensuring your tests do not affect each other.

Blueprints is an interesting way to organize an application. If I were to compare it to Rails, it may seem harder to read because the files are more densely filled with code, but there are also fewer files to go through, which makes it a little easier.

I like that Rails is a full stack framework and you can complete a project from back to front end using one framework. Flask is similar in this way, and it also has all the features and extensions you need to make a full application. 

The main difference is that Flask gives you much more freedom to choose how to build and organize your projects. I think experienced Flask developers probably really appreciate that Flask starts up very simply, and doesn’t make choices for you that you may need to undo or work around if they don’t suit your needs. The trade off is that you have to make your own decisions, and choose what tools you will rely on and how you will build out the application structure on your own.

