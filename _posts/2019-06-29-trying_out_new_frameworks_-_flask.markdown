---
layout: post
title:      "Trying out new frameworks - Flask"
date:       2019-06-29 05:12:41 +0000
permalink:  trying_out_new_frameworks_-_flask
---


I wanted to try out some other web frameworks in different languages to see how they worked and if I would have a preference for one. The first new one I tried was Python Flask.

I had learned Python a few years ago in college and wanted to refresh my knowledge of the language, and learning a popular web deveopment framework like Flask seemed like a good way to do so. Flask, compared to Django, is much simpler, without many preset packages and add-ons. It allows you to choose what you need.

**Flask Setup**

I followed Miguel Grinberg's Flask Mega Tutorial [link](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-i-hello-world ), which explains each step in much better detail and what tools you are using / what the purpose of each step is, but I will go over the steps to provide a brief overview of how a Flask app is created/structured and how it is different/similar to Sinatra and Ruby on Rails.

You will: 
* Install python3 if you don’t have it -> `brew install python3`
* Create a `venv` virtual environment to separate your project’s dependencies from your operating system and other projects `python -m venv myvenv`
* Activate your virtual environment `source myproject/bin/myvenv`  (Deactivate with `deactivate` in terminal) 
* *Be sure to have your venv activated when installing packages, or it will also be added to your entire system*
* Install Flask using pip, python’s package installer 
* Copy the code and file structure outlined to create a simple ‘hello world’ python server
