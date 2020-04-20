# To Start a New Postgress Project

to initializes npm and creates a package.json file setting yes to all basic questions

    npm init -y

how you install dependencies into your file

    npm i --save dependency <== dependency is replaced by the name of the dependency, ex. ejs

# Different Dependencies

### Postgress (pg):

PostgreSQL client for Node.js

    npm i --save pg

we are using pg as our database, and will be building it with knex

### Knex

requires you to have database client installed as well (the pg we installed above for example)

    npm i --save knex

we then need to do:

    knex init

this will create a knexfile.js file

Inside of it, we need to adjust it:
(It should look something like below when you are done)

    module.exports = {

    development: {
    client: 'pg', <=== list the database client you are using

    connection: {
    database: 'knex_lab_one', <== list the name of the database you are using
    },
    migrations: {
    tablename: 'migrations',
    directory: './db/migrations' <== here mirgrations will be saved*
    },
    seeds: {
    directory: './db/seeds' <== where seeds will be saved*
    }
    },

    };

- it is not necessary to create either of these directories beforehand, they will be generate when running the commands

Once you knex file looks good, check your scripts in your package.json file

#### Here are some example scripts to include to make your life easier:

    "start": "node app.js",
        - this would be your start file to run your app.js if you had one
        - you would say write 'npm start'
    "db:create": "createdb --echo <database_name>",
        - an easier way to create a database
        - npm db:create <database name>
        - make sure you're including the database name you've created (if creating) in your knexfile
    "db:drop": "dropdb --if-exists --echo <database_name>",
        - an easier way of dropping a database
    "db:migrate": "knex migrate:latest",
        - an easier way of migrating the latest mirgration files
    "db:reset": "npm run db:drop && npm run db:create && npm run db:migrate"
        - resetting a your database

- when running database, use npm run <script>

### Commands for Knex:

base commands without using the shortform possibly created in your scripts

    knex migrate:make <filename>

makes a new migration file (replace filename with the name of your migration table)
as specified in your knexfile, it will be created inside the db/migrations directories

    knex mirgrate:latest

will migrate any of your unmigrated files
once you've migrated a file you shouldn't change it, either make a new migration or rollback your migration

    knex seed:make <filename>

makes a new seed file (replace filename with the name of your seed)
as specified in your knexfile, it will be created inside the db/seeds directories

    knex seed:run

runs your seed files within the directory

https://devhints.io/knex

- this is a super helpful cheat sheet
