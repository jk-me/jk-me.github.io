---
layout: post
title:      "Top Box CLI"
date:       2018-09-13 16:24:30 -0400
permalink:  top_box_cli
---

For my project I decided to create an application that displays information about current top box office movies. I started by thinking about what information the user would be interested in. What did I look for when I wanted to see go to the movies? 

After reviewing the webpage, I decided on including a summary and a few critic reviews for each movie, along with additional details such as movie length and number of weeks in theaters. 

The webpage I started scraping from was the imdb.com list of top box office movies. The list linked to the information pages for each individual movie, which then linked to a page of sampled critic reviews for each movie. 

![](https://cdn.pbrd.co/images/HDJQ1wQ.png)

I created a CLI that would display a list of movies, then prompt the user to select a number from the list to see more details about that movie.

![](https://cdn.pbrd.co/images/HDJPpfy.png)

It would then display a short summary of the movie and ask if the user would like to see a selection of reviews. The application would then loop through the command menus so the user could view details about different movies and find one that interested them. 

![](https://cdn.pbrd.co/images/HDJPIAA.png)

I used a class to create movie instances which would store attributes for each movie.  Data scraped from the first webpage was then passed to these objects using an attribute hash. Each movie would then scrape data from their indivudual information page for additional attributes.  

I also created a class for reviews, such that each review instance would store a summary of the review, the review score, the publisher and the author (if applicable) of the review. These objects were created similarly to the previous example, by scraping the data and passing it to each object through an attribute hash. The review instances were then initiliazed so that they belonged to the movie which they described.  

After creating the data structure for these objects and scraping the webpages for information, the last step was to finalize the CLI and format the outputted text to be simple to read and interact with. 

