---
layout: post
title:      "Adventure: a Sinatra app to log your hikings"
date:       2018-07-21 20:04:24 -0400
permalink:  adventure_a_sinatra_app_to_log_your_hikings
---


With *Adventure*, users can create an account and keep a log of their hiking trails and see posts from other users. I had fun doing this project, and spend less time than with the CLI data gem project, Wanderer!! I definetely feel more confident in coding. I'll share with you a little bit of the steps that I followed to build this.

![](]https://i.imgur.com/jz3JDp8.png])

**1. Idea and Setup**

I love hiking and I like to keep a log of hiking trails, so I decided to build an app that can help to keep track of hiking adventures. Before setting up the structure, I  made an outline and a sketch of the end product. I used the Corneal gem (it's awesome!!) to generate the project structure. 

**2. MVC: a separation of concerns**

The *Model-Views-Controller* is a popular, and organized way to build frameworks for web applications. The cool thing about this, is that each of the groups will perform specific tasks, and interact with each other in a different way!
 
 *Model*:  Where the data will be saved and/or manipulated. For my project, I decided to build two models: *User* (a user has_many trails) and *Trails*(belongs_to a user).
 
 *Views*: This is where the user is going to interact with the app, is the face of it, the 'front-end'! I used bootstrap references to make it look more appealing!

*Controller*: The controllers will work with the models and the views, it receives data from the browser to the app, and from the app to the browser. I created three controllers: Application Controller, Users Controller, and Trails Controller. The first one handles helper functions and anything related to the homepage. The Users Controller is in charge the */login*, */register*, and */logout* requests, and the Trails Controller works with Create Read Update Destroy(CRUD) of the app.

**3. Testing the app** 

This was the fun part! Making sure that everything was working perfectly . At first, I had a little trouble with the validation. The problem was that I was getting duplicates of usernames, but I fixed when I remember that I didn't add the  `uniqueness: true` in my User model!  Ooops!!


Overall, it was a good project with no major issues. It took me about three days to do the structure, coding, and styling.

Interested in taking a look? Find my code [here](https://github.com/cmlugoce/Adventure)
