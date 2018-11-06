---
layout: post
title:      "Sinatra Project: My Watchlist"
date:       2018-11-06 00:35:05 +0000
permalink:  sinatra_project_my_watchlist
---


For my sinatra portfolio project, I created a web application that would allow users to track movies and shows they were currently watching or would like to watch. Personally, there are so many new and interesting shows and movies to watch these days that I occasionally forget about one or another, or start a show only to forget what episode I stopped at.

I created three models for this app: users, shows, and movies. Users would have many shows and movies, and each show/movie would belong to one user. Shows had attributes for name, current episode, where to watch, and a description (which could also be used for any viewing notes a user might have). Movies had attributes release year, as well as name, where to watch, and description. 

There were also three controllers mainly used for this app, one each for users, shows and movies. The users controller handled user registration and logging in, and utilized the bcrypt ruby gem for user authentication. The shows and movies controllers were quite similar, and had routes necessary to handle CRUD operations for each model. 

I organized the views so that pages would link and redirect smoothly to each other, and I used a simple bootstrap layout to make the app look a bit nicer. After logging in, a user will be able to see their watchlist, which has links to add more items to their list, or view details for existing items.  

![](https://image.ibb.co/g883vA/Screen-Shot-2018-11-05-at-7-33-22-PM.png)
