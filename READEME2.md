# Steps to Complete this Project

## 1 Review [README.md](README.md)
  
## 2 Inspect Files Using File Explorer

- package.json should have 
- sqlite3
- eslint
- nodemon
- cross-env
- bcrypt
- cors
- dotenv
- express
- possibly helmet
- jsonwebtoken
- knex
  
## 3 Dependencies Missing... so install them

- add dependencies 
- npm i
- npm i jsonwebtoken
- npm i dotenv
- 
## 4 Inspect DB in SQL

- get to know schema structure, data, constraints etc
- be sure to check all tables separately
- 
## 5 Add Secret .env file

- build out secrets/index.js
- build .env contents
- bring into root index.js

## 6 Configure Debugger 
- Note I DO NOT USE THIS MYSELF... but you may find it helpful

-  [Helpful Debugger restart using Nodemon](#helpful-debugger-restart-using-nodemon)

``` json
{
    "version": "0.2.0",
    "configurations": [
        {
            "type": "node", 
            "request": "launch",
            "name": "nodemon",
            "runtimeExecutable": "nodemon",
            "program": "${workspaceFolder}/index.js",
            "restart": true,
            "console": "integratedTerminal",
            "internalConsoleOptions": "neverOpen",
            "env": {
                "debug": "app:*",
            }
        }
    ]
}

//be sure nodmone is installed globally 
//npm i -g nodemon
```

## 7 Stubb out server.js
- for this project it was already done for us

## 8 Inspect and stubb models.js
- Start with users-models.js
  - to do this you may need to inspect the routes first.
  - in the real world you'd have to stubb out the route next and then start testing each rout and model stubb before moving forward. 
- __find()__ needs this SQL editor solution
- 
    ```sql
    select
    user_id,
    username,
    role_name
    from users
    join roles on 
        users.role_id = roles.role_id;
    ```
- 
    ``` sql
    test http :5000/api/users
    ```
- notice the test just hangs without next() in auth-middleware.js in restricted. Add it if you didn't already
- __findBy(filter)__
    ```sql
    select
        user_id,
        username,
        password,
        role_name
    from users
    join roles on 
        users.role_id = roles.role_id
        where user_id = 1;
    ```
- __findById(user_id)__ 
  - go to users-model.js to see what I did. 
  - test it .. remember to put next() in the const only = role_name method of auth-middleware
  
## 9 Build out Middleware
- start with validateRoleName
- with that build out you can jump to auth-router.js POST /register endpoint and complet it. 