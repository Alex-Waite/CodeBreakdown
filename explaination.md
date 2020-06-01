## Code Breakdown: Node App

In this homework task I will be looking at a woking application and breaking down its components to understand how it works

# Part 0: Universal Concepts

In many files of the code you will notice lines of code that look like this: _var X... = require("Y...")_, These scripts are module imports, this is how developers import node modules to their code.

Node modules are basically _Modules_ of code that are used to perform a certain task (eg, Inquirer node module is used to ask a user questions in the console so the developer can handle their responses), modules are used to save time in programming, there is no point in spending your time inventing a wheel if someone has already done it and all you need is a _var wheel = require("wheel")_ in your code to use it.

These modules can be created by the developer for use in the project or they can be imported from online.

package.json and package-lock.json are files that hold the details for these modules so the computer can read them.

# Server.js: The server connection

The _server.js_ file found in the main folder named _Develop_ is used to set up a connection to an express server which basicaly means it creates an environment for http requests and functions to run.

The server.js uses the express module to set a server up on the port 8080, this server will be used to "initialize" the app.

# Config Folder

The config folder contains a middleware folder with _isAuthenicated.js_ inside, this files is a basic module that checks to see if the user is signed in or else it redirectes them to the "/" route which is the login/register page.

The config folder also contains a _config.json_ file, This file is used to connect the application to the database, the 3 "branches" named development, test and production are used to filter what the website user sees as oposed to what a dev who is testing new changes sees. It is best to have a working state of the app live while the devs test on their own branch

lastly the config folder has a passport.js which contains the node module "passport" and uses that module to set up a check and validation for a user login, it takes user input and checks the database for details matching the user input if a match is found the user is logged in and if no match is found the error is displayed, this file is exported for later use.

# Models Folder

It is difficult to read what the index.js file is doing however it is clear that it is using sequelize to set up a database of some sort and on line 8 you can see that the config.json file made earlier is now being used, this is imported as a module.

The user.js file is used to create a sequelize data table containing user details, it uses the bcryptjs module to encrypt user passwords for security purpose, this is also imported as a module.

# Public Folder

This folder is used to store all the thing that the user will be able to see, things like css, images, some js and html usualy go in here

There are 3 .html files in the public folder, these are all used to set up the structure of the webpages that the user will be sent to such as the login page and sign up pages

The stylesheets folder contains a style.css file which is usualy used to decorate and style a webpage so it doesnt have a basic html file look, in this case the style.css is only used to put the contents of the sign in and register forms 50 pixels away from  the top of the view window

The js folder contains 3 .js files which all correspond with a html document in the public folder, these .js files are used to communicate what happens on button clicks and form submissions and things and communicate what goes in the requests that are sent to the back end.

# Routes Folder

The routes folder is used as a form of pointer stystem for the computer to read where it should be sending the user/data depending on the requests it recieces from the front end

The html-routes.js file is used to create instruction for the computer so that when it recieves a request it knows what to do with it, an example in this instance is if the server recieves a GET request of "/members" the computer will check if the user sending the request is signed in through the use of the isAuthenticated module which was made in the config/middleware folder. the computer will then make a decision on where to send the user, if they are signed in they will see the members page, if they are not they will be redirected to the sign in page.
This restricts the "/members" route to users who are signed in only