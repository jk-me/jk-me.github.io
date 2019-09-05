---
layout: post
title:      "Python Web Scraping"
date:       2019-09-05 16:20:01 -0400
permalink:  python_web_scraping
---


A quick post on Python3 web scraping script using the BeautifulSoup4 Python library.

[Link to Tutorial I Used](https://towardsdatascience.com/how-to-web-scrape-with-python-in-4-minutes-bc49186a8460)

This blog post explains the process pretty well, I will just go over some things I did differently and thoughts I had while doing this tutorial.

The author uses a Jupyter Notebook to write her script. It is a popularly used python IDE, more on python IDEs vs. text editors here: https://www.datacamp.com/community/tutorials/data-science-python-ide 

“Jupyter Notebook provides you with an easy-to-use, interactive data science environment across many programming languages that doesn’t only work as an IDE, but also as a presentation or education tool. It’s perfect for those who are just starting out with data science!” 

I wrote the entire script in one .py file in atom and ran it with python in the terminal. Using the command:
`python3 mta-scraper.py` (Need python3 installed)

 Link to my github: [git](https://github.com/jk-me/py-mta-turnstile-scrape)

You may need to install the BeautifulSoup package using pip `pip3 install beautifulsoup4` It might be a good idea to install it in a virtual environment, but it seems innocuous to install this package globally into my machine, so I’ll keep it for now…

(I’ve written a little bit about venv in my previous posts on Flask project setup)

The last step in the script, the for loop, iterates over the relevant data links and uses the `urllib.request` module to save the data into your current directory with a relevant filename. It will actually download the data from each link and save it into your folder as .txt files, which in this case, look very similar to csv files. 

It’s important to note that a `time.sleep(1)` is included in the for loop. This pauses the code for 1 second between iterations, slowing down the pace at which data is downloaded. This will prevent the website from flagging you as spam or as a bot, as some sites do to prevent overloading the server.

`time` is a python library that must be imported into your script

Beautiful Soup is a python library used to parse HTML and XML files. It’s documentation is quite clear and easy to understand: [docs](https://www.crummy.com/software/BeautifulSoup/bs4/doc/#)

In this script a BeautifulSoup object is created, which represents the entire html page. It then uses the `find_all` method to find all the link tags in the page. It is currently using the `html.parser` included in python’s standard library, but can also use third party (html and xml) parsers.

Urllib.request.urlretrieve - copies object that a url points to as a local file

requests is the python standard http request library. Calling a request method with a url will return a response object, which will show its status code when printed. `respObj = requests.get(url)` 

There are many methods used to interact with this object. Here `respObj.text` is called to return the html response as a string. If JSON data is returned, it can also be parsed as `resp.json()` More details: [realpython](https://realpython.com/python-requests/)

