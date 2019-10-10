---
layout: post
title:      "Ruby Cli Gem - Live Version"
date:       2019-10-10 04:04:22 +0000
permalink:  ruby_cli_gem_-_live_version
---


Most of the projects completed through Flatiron’s Full Stack course are web applications using Sinatra or Rails which can be hosted on sites like heroku or netlify. To show a live version of the Ruby CLI project, I decided to publish my app as a gem and then demonstrate its use with a repl.it project. 

Gems are published through rubygems.org
Repl.it is a site for building projects using many different frameworks and languages through an online IDE

[My Repl](https://repl.it/@jkam17/top-box-office-cli-gem)
[RubyGems docs](https://guides.rubygems.org/make-your-own-gem/)

Helpful commands for gem building/publishing:
$`gem list`  //check what gems are installed
$`gem build app_name.gemspec`  //builds gem (app_name-0.1.0.gem)
$`gem push app_name-0.1.0.gem` //publish gem, will need a rubygems.org account

After creating your project, create a `app-name.gemspec` file and add the required specifications.
[Gemspec Reference](https://guides.rubygems.org/specification-reference/)

Make sure you have the required specs filled out, as the build command will create your gem based on this. Your version (0.1.0, etc.) must be unique if you are updating your gem, otherwise it will not be published. 

Before building, make sure your `lib` directory has a file named `app_name.rb` which sets up your app environment, as you should have based on the CLI project requirements. This file must have the same name as the gem’s `spec.name`, as it is what ruby will look for when you `require` the gem after installing it elsewhere. Check the `Name Your Gem` section of RubyGems docs for more tips.

Run `gem build app_name.gemspec` , and a new `.gem` file will appear in your project’s root directory. This is unique to each build, so after any modifications to your gem's code or the gemspec, you must run gem build again. Subsequent calls of gem build will require you update the gem version as well, or you can delete the old .gem file (probably not recommended if already published)

If you run into a build error, it may help to `git add .` your files before building.

You should be able to test your gem on your local environment. `gem install app_name` in your terminal. (tip: `gem list` to check install) Then run `irb` and `require 'app_name'`. You should be able to execute your CLI application as `AppName::CLI.new.call`.

This is similar to how it will be done on Repl.

Then run `gem push app_name-0.1.0.gem` to publish to  your rubygems.org account. You will be prompted for account credentials.

Create a new repl.it project in Ruby, and add a `Gemfile` with the following:
``` 
source 'https://rubygems.org'
gem 'app_name' 
```

Then in the main.rb file, add `require ‘app_name’` and run your cli execution command. `AppName::CLI.new.call`. Upon run, the repl will install the gem and execute the main.rb script to show your CLI app.

Tip: To open the command line in Repl, press F1 and type ‘open shell’



