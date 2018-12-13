---
layout: post
title:      "Rails Project: MyBar"
date:       2018-12-12 19:43:09 -0500
permalink:  rails_project_mybar
---


For my rails project, I decided to create an app to manage an index of bar drinks. Users could sign up, add drinks to a master list of drinks, write reviews for them, and even save their favorites to a personal drink list. Users could view the full list of drinks, or filter it to view complex drinks with 4 or more ingredients, or simple drinks with 3 or less. A user could also see the list of ingredients currently used in all drinks, and then select one to view drinks that were made with that ingredient. 

I created models for users, drinks, ingredients, and reviews. For the model associations,

	Users would:
* have many reviews
* have many (favorited) drinks through a users_drinks join table 


	Drinks would:
* have many reviews
* have many users through the users_drinks join table
* have many ingredients through a drinks_ingredients table
	Ingredients would: 
* 		have many drinks through the drinks_ingredients table 
	Reviews would:
* 		belong to a user 
* 		belong to a drink

I used bcrypt to for user authentication, in addition to omniauth to allow login through facebook. I also added a simple bootstrap layout using this guide on Github: https://github.com/twbs/bootstrap-sass

One of the biggest difficulties I had during this project was just generally feeling overwhelmed by dealing with so many files and and having to add many specific features to complete it. Adding validations and scope methods to models, error checking controller methods, working to consistently use partial layouts, forms and helper methods to simplify code while trying to make sure they were not being used redundantly was definitely a challenge.
