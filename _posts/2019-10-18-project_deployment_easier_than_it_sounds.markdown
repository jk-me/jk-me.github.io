---
layout: post
title:      "Project Deployment: Easier than it sounds!"
date:       2019-10-18 23:32:32 +0000
permalink:  project_deployment_easier_than_it_sounds
---


A quick overview of how to deploy a Rails or React application on Heroku. This isn’t a step-by-step guide, but rather a post to show that deploying is not as scary or difficult as it looks. A lot of things happen when an app is built and deployed, but there's plenty of room for stumbling forward and learning.

You will need a heroku account, as you deploy by pushing your git repository to heroku from your terminal and it will require account credentials.

For React-only projects, there is no configuration needed! Basically you can run `heroku create` and `git push heroku master` and your project should be online.

Overview for Rails:
* Use a postgres database - use `gem pg` (make sure to bundle install)
* Specify configuration (in `config/database.yml`) as postgres
* Good idea to test your app locally so that it is working with postgres
* Git commit all final changes before attempting to build
* `heroku create`
* `git push heroku master` (doesn’t push to your regular remote so you will need to do so eventually)
* If your build fails, read the error messages carefully to see what went wrong. Usually it’s a pretty simple fix of one or two lines of code (or removing yarn when I already have npm)
* If your build succeeds but your app doesn’t work, check the logs to see the issue (I probably forgot to migrate my database)

Helpful notes:
* `git remote -v` //shows remote repositories, including heroku after heroku create
* `heroku run rake db:migrate` //migrates database for heroku app, can also db:seed
* `heroku apps:rename new_app_name` //renames app -> url and heroku git repo
* `heroku logs --tail` //shows heroku logs, examine carefully when running into errors

You may need to add a Procfile to your root directory, but in many cases heroku can detect your app’s configuration and create it for you. You will probably need to add it in the case that your Rails and React components are coming from one repo.

Helpful Links:
* https://devcenter.heroku.com/articles/getting-started-with-rails5
* https://blog.heroku.com/a-rock-solid-modern-web-stack
* For "Asset Pipeline" Issues: https://devcenter.heroku.com/articles/rails-4-asset-pipeline
