---
layout: post
title:      "When Hobby Meet App(y)"
date:       2018-04-13 02:59:17 -0400
permalink:  when_hobby_meet_app_y
---


For my Sinatra Portfolio Project I decided to make a web app that let the user create, edit, or delete a list of Magic the Gathering deck and also see decks that other users has created. It is called Magic the Gathering Deck Organizer or MtG: DO for short. 

Initially I thought this app will have a simple model system. A user have many decks and decks belong to a user. And the other association would be decks have a many to many relationship with cards. But then I was stumped because I wasn't sure how to implement a model that have many to many relationship between deck and cards and also remembers the quantity of each cards for each specific deck. Then I remembered that many to many association uses a join table so I decided to use the deck_cards join table to store the quantity of each card in a particular deck. With that problem fixed, I continued to create the web app one page and route at a time. 

Everything was coming along so well until I hit the new deck page. Here I had to decide whether to add each unique cards in the deck by their own input form or use a textarea to add them as a massive text. An individual input for each card would be great since I can get the data to add to my database a lot easier, but I decided it would be too awkward having twenty or more input lines just to add the cards for the deck. So I decided to use textarea for this task. Since textarea would return a multiple lines string for my deck list, I needed to create a method to parse the string into each individual card and their quantities, then find or create an object of that card, and add those cards to the deck. 

This parser was by far the most complex thing in this app. To do this I specified a format on how the deck list should look like: There should only be 1 card per line, and the quantity of each card needed to be specified in the beginning of each line followed by x. This way I can divide the string into an array of lines and each line consist of a card and the quantity of that card in the deck. If the deck list doesn't follow this format or the user typed in the wrong card name then an error will occur and it will redirect the user back to the page without creating the deck. 

Once the parser method was done and debugged, I continued creating the rest of routes and pages of the app. Once all the routes was created with their appropriate pages, I decided to stylized the app since it was very hideous without any css. I decided not to use bootstrap since I don't really need much of its functionality and instead made a new stylesheet from scrap. 

And with that I have just completed my Sinatra app pending review of course. If you would to check out my app you can visit the [repo page](https://github.com/rockychiang/mtg_deck_organizer), clone it and run it on your own local server. If necessary you can also watch my demo of the app [here](https://youtu.be/g99BkszLstI). Thank you for reading and until next time. 
