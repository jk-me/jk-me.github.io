---
layout: post
title:      "Rails w/ Javascript Project"
date:       2019-02-08 19:24:09 +0000
permalink:  rails_w_javascript_project
---


The Rails and Javascript project required students to build on their preexisting rails project and add dynamically loaded javascript elements. In my project, the my-bar application from my previous blog post, I added several javascript features including loading a form, submitting the form, viewing the next record in a database model, and showing additional data for a record, all without without redirecting or loading a new web page.

In more detail, these features were:
* A link to load full review content for lengthy reviews in a table (normally it is truncated), as well as a link to shorten the content as desired.
![](https://media.giphy.com/media/1gdqKgs6csuyn004bo/giphy.gif)

* A link to display some details of a selected drink from an index of drinks on the same page. It allows users to quickly view information about the drink before they decide to see its full information.
![](https://media.giphy.com/media/1jY3pAEqg0DqVcgIkF/giphy.gif)


* A link to load the full information of the next drink in an index. This feature also works with ingredient and user nested routes, so the user can browse quickly browse through their favorite drinks, or through drinks that contain a specific ingredient
![](http://)

* A link to append a form onto a drink’s information page to add a new review. This form is then also submitted via javascript and loads dynamically onto the review table on the current page
![](http://)


