# To start a new Express project:

    npm init -y

initializes npm and creates a package.json file setting yes to all basic questions

    npm --save-dev nodemon

adds nodemon as a dev dependency
also have to add "start": "nodemon app.js", to your scripts in the package.json file

    npm i --save dependency <== dependency is replaced by the name of the dependency, ex. ejs

how you install dependencies into your file

# Different Dependences:

### Express

express is a node framework

    npm i --save express

in main js file, need to include:

    const express = require("express");
    const app = express();

### Express Build in Middlewares

#### express.static

included in express as a method, don't need to install or require
this allows you to serve static files such as images & css files

    express.static(dirname)

dirname is the name of the file that where you are storing your static
it is convention to use a 'public' directory for all of your static assets

#### path.join

this is a node.js method
it allows you to make sub folders inside of the specifed folder that your express.static is accessing
because its a node method, in main js file, need to include:

    const path = require("path");

### To include all of the above:

    app.use(express.static(path.join(\_\_dirname, "public"))); <== those \ are not included

    express.urlencoded

included in express as a method, don't need to install or require
A new body object containing the parsed data is populated on the request object after the middleware
This object will contain key-value pairs, where the value can be a string or array (when extended is false), or any type (when extended is true).

To include above:

    app.use(express.urlencoded({ extended: true }));

### EJS

    npm i --save ejs

its a templating engine used by node.js
in main js file, need to include:

    app.set('view engine', 'ejs');

this allows the embedded js, and the ability to use ejs files when creating your pages
it is convetion to put all your ejs files inside of a 'views' directory within the project

### Morgan

    npm i --save morgan

morgan is a node.js middleware
in the main js file, need to include:

    const logger = require('morgan');

    app.use(logger('dev'));

a logging tool for working with http servers
allows us to log request, errors and more to the console

### Cookie-Parser

    npm i --save cookie-parser

cookie-parser is a node.js middleware
in the main js file, we need to include:

    const cookieParser = require('cookie-parser');
    app.use(cookieParser());

parses cookies attached to the client request object

Creating your server:

you need to use app.listen()

Example:

    const PORT = 3000;
    const ADDRESS = 'localhost';
    app.listen(PORT, ADDRESS, () => {
    console.log(`Server listening on http://${ADDRESS}:${PORT}`);
    });

Don't forget to create a .gitignore file to ignore node.js & either MacOS or Linux
