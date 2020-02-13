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

## Heroku

- Create New App
- on Deploy tab, there's a section called deployment method and github is what you want to use

  - in order to do that, we have to connect heroku to github
  - click on connect to github button that will appear once you select github as deployment method
  - search for repo
  - choose branch
  - click on enable automatic deploys
  - clicking on deploy branch under manual edploy will push branch first and begin deploying which you can see in overview tab

- to check logs

  - in more button, click view logs
  - app is not listening in a port that is not supported by heroku (cause of error)
  - heroku will set an env variable named port

- bug with knex
- heroku is setting NODE_ENV a value of "production" instead of development
- delete `const environment = process.env.NODE_ENV || "development"
- or decalre NODE_ENV to "development"
- hard code environment to equal development

Default port for https is port 43
