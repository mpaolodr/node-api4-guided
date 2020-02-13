CICD

- continuous integration continuous deployment

Add `start` in scripts in package.json

- when we configure heroku to automatically deploy our app from github, heroku will look for a package.json file
  and if there is one, it will look for a script called "start"
- that's how heroku knows how to start our application

Put `node index.js` inside `start` script

Hard coding port number will not work so we'll have to find a way to make heroku give us the port

By convention, all env variables are named in all uppercase letters

- to create new variable in terminal `export VAR_NAME=value`, to unset, `unset VAR_NAME`
- we can access env variables from within our application through an object called `process` and a property called `env`(process.env)

Install dotenv `npm i dotenv`

- on your index.js

  - either:

            const dotenv = require("dotenv");
            dotenv.config();

          or

            require("dotenv").config();

- create .env file on your root directory

  - set up your env variables `PORT=5000`

- check if .env is included in gitignore
