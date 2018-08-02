---
layout: post
title:      "Rails magic: a cheat sheet of important rails command (part 1)"
date:       2018-08-02 21:00:27 +0000
permalink:  rails_magic_a_cheat_sheet_of_important_rails_command_part_1
---


Recently, I've been working on the Rails section and I can't believe how awesome (and tricky) it is! Rails is like Hogwarts, a magical place where great things and crazy things can happen. In order to enjoy Rails, we must know some fundamental commands. So, for this blogpost I decided to share a list of the most important Rails commands.

<p align="center">
   <img width="460" height="300" src="https://i.imgur.com/slbNwiA.gif">
</p>
	
 
 
**Note**: To run these commands you must cd to the root directory (exception:` rails new`)!

| Command   | Concept    | Notes    |
| -------- | -------- | -------- |
| `rails new `  name  |create a new application      |     With this command you can create the skeleton of your app.
| `rails server`  or   `rails s`  | start the server   | Start the server( similar to 'shotgun'). You'll be able to acces it via **localhost:300** . To stop the server , **press Ctrl +C**  |
|`rails g scaffold` *name attribute:type*| Scaffold | The magic trick! It generates controllers, models, and views. Also, it creates a new resource, edit, show, and delete.     **Note**: While this is an awesome trick, I'm staying away from it because I like to build my models and controllers from scratch!|
|`rails g model` *name attribute:type*   | creates a model and migration   | Also, it creates a model file that will inherit from `ActiveRecord::Base`.   It creates a database migration that will add a table and columns with the attribute information|
|`rake db:migrate` | Migrations  | This command updates your database. Make sure to run this command everytime you add a new migration!!|
|`rake routes`| shows existing routes| It shows a list of available routes in your application. It is a lifesaver!!|

I use these commands a lot, and they have made my life much easier!! In my next post I will share a list of the basic structure of a rails app! 

For more info, you can check out [this](http://www.pragtob.info/rails-beginner-cheatsheet/) awesome tips!

