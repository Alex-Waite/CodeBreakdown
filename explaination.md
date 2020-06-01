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

