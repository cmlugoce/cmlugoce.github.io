---
layout: post
title:      "Hiking with the CLI Data Gem"
date:       2018-07-02 15:25:38 -0400
permalink:  hiking_with_the_cli_data_gem
---

I can't describe how I feel after finishing this project!!! 

The CLI Data project was challenging and fun. I feel more confident writing code and scraping with Nokogiri (one of the greatest things in the Universe). Let me tell you a little bit about my project structure:

**1. Idea and setup**
        
I love hiking, and traveling, so I decided to build *Wanderer* a CLI that will inspire the user to go hiking around  the world. Watching the CLI data gem walkthrough video helped a lot! *Wanderer* is an app that offers a list of the top 15 long-distance hikes around the world. After the user selects the hike of their interest, the program will offer the distance and review of the hike. 
	
**2. Create the Gem: Wanderer, and CLI**

At this point, I was following the steps from Avi's video.  Creating the gem with bundler was the easy part (it look like a magic trick), all the files that I needed were include with the gem. I set up my environment and tested the `bin/console` and `bin/wander` After this, I built a fake CLI to test how wanted the information to be projected. I created the Wander class that was in charge of scraping and iterating the website.

**3. Scraaaaapeeeee!!**

Scrape! Hmm! Mixed feelings about this hahaha! I spent most of my time scraping. I had to review the lessons on Scraping with Nokogiri. I had a list of 4 websites to scrape, and none of them work well, so I went to myy friend Google and searched for another website. Luckily, Fodors website is user-friendly, and most importantly, scraping-friendly. Selecting the CSS elements and iterating them was fun. After having this part completed and tested I felt great, and relieved.

**4. CLI**

All the scraping is done. So it was time to update my cli.rb file and test it. I did run in some problems (typos everywhere hahahha), but nothing out of control. I added another dependency to my gem: Colorize. With colorize, I added some colors to my CLI, to make it look more appealing. 

**My take away from this project**

Building the CLI project was fun. It definetely tookk way more time than I thought, mostly because I wasn't sure of my idea, and the scraping hahaha! After seeing the end product, I have to say that I'm getting comfortable in wrting my own code, and that I'm excited and looking forward for more challenges!

Curious about my CLI gem? Check out my video  :)


[https://youtu.be/pUG2tOeyU7s](http://)
