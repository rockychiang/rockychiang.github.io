---
layout: post
title:      "One Small App in Ruby, One Giant Leap for Me"
date:       2018-03-25 04:41:32 +0000
permalink:  one_small_app_in_ruby_one_giant_leap_for_me
---


So for my CLI project, I made a Ruby gem that list out all the new TV episodes that are airing in that particular day and give more information about a specific show if the user would like to know more about them. 

Initially I thought this was gonna be an easy project, I only have to make a CLI class to control the interface, a show class to organize and store the information of each show, and two scrape method: one for the list of the new TV episodes and another one to get  further information for a particular show. Everything was going as planned until I started scrapping the website that I chose for this project. 

The first hurdle appeared when I was scrapping the list of show for the day. The website I chose listed all the shows, both recurring and new episodes, that are airing on that day. Since I want my app to only show new episodes and not a recurring one I knew I had to figure out a way to fix this. The problem is that the webpage does not differentiate new episodes from recurring one. So to separate them I had to scrape the information from each of the show's webpage. This slow down the initial load time of my app from several seconds into a couple of minutes, which bothered me. However, since I could not think of another way to list only the show with new episodes and I could not find any other alternative site to do what I want, I decided to "bite the bullet" and continue with my project. 

Another hurdle emerged when I was scrapping more information for the show. While some info like the summary or the genre are easily scraped, others are not as trivial. They are hard to extract because some of the text are not enclosed in any specific attribute, such as a class, id or even span, but rather they exists just as a text inside a generic div container. So to get those text I had to get all the text inside those div, separate them apart into text in an array and figure out whats the index number of the specific text that I need. Fortunately the number of text in the general div are are pretty consistent across the different show's webpage so this method actually works for all the show. 

Once I solved those problems, a couple hours of bug fixing, and a quick google on how to publish my gem into rubygems.org, I finally finished my first project pending the review of course. Overall although the project was not easy as I thought it would be, it wasn't overly difficult either. If you would like to check out my app just install it on your machine using `gem install new_show_tonight` command and enter `new-show-tonight` on your command line. 
