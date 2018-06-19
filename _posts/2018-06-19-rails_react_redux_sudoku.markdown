---
layout: post
title:      "Rails + React + Redux = Sudoku?"
date:       2018-06-19 21:04:48 +0000
permalink:  rails_react_redux_sudoku
---


For my React project I decided to make something I have been wanting to make since I started this journey, a game app. Specifically I have created a simple Sudoku app where user can compete for the best time with other users. There is no login required to play however user do need to give their username if they want to compete in the leaderboard. 

When I started this project I knew I wanted to create a simple app where anyone can use without any prior knowledge of the app. However this would also limits what features I can add. So I decided I will start with a simple app and add further complexity as I add other features. To do this I started by creating the React and Redux side of the app leaving the Rails API for last. 

First I created a simple homepage component that controls the routing of the app using `react-router-dom`. Other than the homepage only two other routes are available: '/game' and '/leaderboard' each with their own components. Next I started on the meat of the app, the game itself. To generate the puzzle and the solution I decided to use a third party [puzzle generator](https://github.com/dachev/sudoku) for Node for now. I do plan to change this by making my own puzzle generator in the future so I can add a varying difficulty mode. 

The game component itself is made up of several smaller components: the board component, the button component and the userform component. The board component consist of a table with nine rows and nine columns and each cells are filled with either a fixed number from the generated puzzle or an input component that updates the store state whenever a change occurs. Once the board is filled it will check whether it matches the solution or not. If it does then a conratulatory message will appear with a form asking for the user's name. If the user decide to input their name, then their game will be stored into the database and they will be redirected to the leaderboard page. 

Other than the board and the userform, the game component also have three buttons that is related to the board state. The first button will generate a new puzzle, update the board, reset the timer and reset the status of the game, essentially reseting the game state with a new game. The second button reset the board to its initial state by removing any user input and reset the game status but not the timer. The last button solve the current puzzle but it will also lock the board so that the user cannot interact with the puzzle anymore. This button also disable the reset button so the user cannot use it to cheat the leaderboard. 

With the board component completed the only thing left to do is to create the leaderboard component. It is a simple component that fetches the top ten games from the database and show it in a table format. It uses the `thunk` middleware to make use of an async actions to update the state when recieving data from the database. 

While at this point the app is up and running, I plan to further improve it in the neer future by adding other features such as multiple difficulties and a save and load system. To follow the progress of my app please check out my [app](https://github.com/rockychiang/) here or watch a [demo](https://youtu.be/Jc8HQQBW-_c) of my app to see how it works. Once again thank you for reading and until next time.
