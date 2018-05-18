---
layout: post
title:      "Everything is Better With Javascript"
date:       2018-05-18 00:50:51 +0000
permalink:  everything_is_better_with_javascript
---

When I was coding my [Rails app](https://github.com/rockychiang/manga_list_app), it always felt like something was missing. The app was great and interactive but some features felt clunky and slow. Due to the lack of javascript, the app had to reload the page every time the user clicks a button to submit a form. So when I started the Rails with Jquery Front End, I knew exactly which features I would like to update. 

To give some background information, the Manga List app lets the user track their manga collection, record progresses for each manga in their collection and add review & rating to each manga. So on the user profile page as seen below there is a table that tracks the user's collection and their status (progress) for each manga. Previously I programmed the field so that it would submit the form every time there is a change in the text field. However, it would submit the form and then reloads the page every time this happens, which makes for a clunky interaction. So one of the thing that I did in this project is updating this feature to send the request via ajax instead.

<a href="https://imgur.com/yXd5fgF"><img src="https://i.imgur.com/yXd5fgF.png" title="source: imgur.com" /></a>

To do this I added an event listener to the page to wait until one of these events happen. Once they are triggered it captures the field's value along with other hidden form inputs, serialized them into a string, send an ajax request to the server and submits the form. The server then sends back a response in the form of JSON and proceed to change the content of the page as necessary. 

For example, if a user changes their manga status from "Never Read" to "Reading", a new text field next to the status drop-down will appear. The text field itself is a form disguised as a plain text field and it lets the user tracks their progress by recording the current chapter that they are reading. In order to properly add this form to the page, I use the Handlebars template. 

Handlebars is a javascript library that lets developer create an HTML template in javascript, similar to an ERB partial in rails. It creates the desired snippet of HTML whether it is a form, button, div, etc. by injecting a javascript object with the correct keys and values into the template. It is very useful when used in conjunction with Jquery to make your web app more interactive. 

The example above is but one of the many features in my app that utilizes Jquery to make it more interactive. To find out more about these features please check out my app [here](https://github.com/rockychiang/manga_list_app) or watch a [demo](https://youtu.be/Hcom4fokZvw) of my app to see how it works. Once again thank you for reading and until next time.


