---
layout: post
title:      "Train #3 Has Left The Station"
date:       2018-04-26 20:10:24 -0400
permalink:  train_3_has_left_the_station
---


For my Rails project, I made a web app that lets the user tracks their manga collection, add reviews, rate manga, and see other user's collections. I dub this app the most creatively named app possible: Manga List. 

Rails is such a great framework that does most of the grunt work for you and makes it easy to create a web app from scratch. I started this project first by mapping the tables, the columns of each tables, and their association with each other. And once I mapped this out, in only a matter of minutes, I was able to generate all the models and migration tables that I needed for the app all using the Rails generate macro. 

Next I proceeded to map out all the URL and the routes needed for the app. In the process of mapping this out, I also made a checklist which tracked my progress and let me know which pages are completed and which one still need more work. The checklist also made it easier for me to see which pages will be open to public, and which one can only be accessed by the user or admins. Again I was able to set all this up in a short amount of time all thanks to Rails generate macro. 

Once all the groundwork has been set, all I have left to do is create the views and code the route's logic one page at a time. First I implemented a standard registration/login system that only accepts unique email address for each account and uses the bcrypt gem to encrypt and authenticate each user's password. I also implemented a third party authentication system (Facebook) using the OmniAuth and OmniAuth Facebook gem. 

The rest of the app I think is a pretty standard for a content management system. In this case, a user has many collections and many manga through their collections. They can also add their statuses for each manga in their collection, or rate and review the manga in their collections. All of which is being tracked by the collection table. Lastly, I made it so only admins can create and edit manga so that the database can be as accurate as the admin maintain them to be. 

All in all this app was a great experience in learning how to create a content management system usings Rails which I enjoyed very much. If you would like to check out my Rails App you can visit the [repo page](https://github.com/rockychiang/manga_list_app), fork it, clone it and run it on your own local server. If you need any help with the app you can check out my video demo of the app [here](https://youtu.be/Hcom4fokZvw). Once again thank you for reading and until next time.
