---
layout: post
title:      "Parks-book: a rails app"
date:       2018-08-18 17:15:54 +0000
permalink:  parks-book_a_rails_app
---

 
 For the rails project portfolio, I decided to built a website, [Parks-book](https://github.com/cmlugoce/parks-book), in which users can log their parks & trails visits. Users can log in and signup in the "normal way" or they can do it with their Facebook credentials. 
 
 ![](https://i.imgur.com/9z4ILJu.png)
 
 The following is the project structure of the rails app:

 *Models* : User, Park, Trail, and Comment
 
 *Associations*: User has_many parks, has_many comments, and has_many trails through parks.
                                 Parks belongs to users, and has_many trails.
																 Trails belongs_to parks, and belongs_to users.
																 Comments belongs_to trails, and belongs_to users
																 
*Third-party login*: For the third-party login, I used the gem omniauth-facebook

![](https://i.imgur.com/UiJ56tE.png[)
	
After the signup or login, users will be directed to their profiles in where they will see their parks visit.  Every user can upload photos from their visits, and they can see what other users are posting. To follow along with my associations, in order to create a trail, the user has to have a park, this will help to keep their profiles and website more organized. 
For the trails section, they users can also upload photos, and aditionally, they can comment on other users trails. Also, I added three search filters to help users to save sometime in scrolling on the trails and parks index. 
![](https://i.imgur.com/7X184xn.png)

This project took me more time than expected.  I had some struggles in setting up my associations. I did a lot of research, read the Rails Guide like 10 times, and visited Stackover flow many times. I feel way better about coding in Rails, and I had the chance of searching and working with other gems like Carrierwave, which made my life a bit easier! I'm planning on keep updating my project and start adding more functions to it! 




