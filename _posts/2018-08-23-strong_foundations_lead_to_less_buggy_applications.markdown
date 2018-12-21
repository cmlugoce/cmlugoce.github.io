---
layout: post
title:      "Strong foundations lead to less 'buggy' applications"
date:       2018-08-23 19:58:48 -0400
permalink:  strong_foundations_lead_to_less_buggy_applications
---


Just like houses need a strong foundation, an app needs a strong foundation to work well. For a while, I thought that I had functional understanding of how to set up ActiveRecord Associations (especially many-to-many relations), but it wasn't until I started to explain to relationships in my Rails Portfolio App that I fully realize that something wasn't clicking. I had to take a few steps back and read, write, practice, and verbalize (my mantra). In this post I will focus on the `has_many  through:` !

**Associations**

  The simplest way to define this concept is that an *association* is a connection between two Active Record models. These relations help to make operations like creating a new post to an existing author object easier. Let's look at an example of an app without associations:

![](https://i.imgur.com/0ZQwf2x.png)

If we want to add a post to an existing user we have to do this (kind of annoying):

 ![](https://imgur.com/vcd6Dcx.png)
 
 When we take advantage of the Active Record Associations we declared a connection between the models, and do more operations like create, destroy, update, etc more simpler,  and faster!! 
 
 ![](https://imgur.com/KUwF4bg.png)
 
 ![](https://imgur.com/s0OIKhu.png)
 
 **Many-to-many relations: has_many :through**
 
  There are six types of association, but I want to focus in one, the one that I've been struggling a little with : `has_many  :through ` . From the [Rails Guide](https://guides.rubyonrails.org/association_basics.html) we get this information: 
	
 	A` has_many :through` association is often used to set up a many-to-many connection with another model. This association indicates that the declaring model can be matched with zero or more instances of another model by proceeding through a third model.

I remember reading it a couple of weeks ago and thinking that it was cool. But today, I read two or three times, and it finally click on my brain. I had to practice by creating a simple diagram and an app. For the practice/example I thought about teachers, students, and parents:

![](https://imgur.com/giQToWs.png)

![](https://imgur.com/dCW1Gdw.png)

With this association you can use the same [has_many](https://guides.rubyonrails.org/association_basics.html#has-many-association-reference) methods and create join models (e.g. `teacher.parents = parents` ) 

**My lesson**

No matter how simple is the concept, always review and practice it. I struggle with this a bit in my Rails project, but I'm glad that it happened because it gave another chance to review and finally get a grasp of it! Now that I understand it a little better, I will continue on improving, and fixing the associations of this project for the Javascript section.


