``Installing npm & package control in sublime text``

1. Install node and npm (http://nodejs.org/)
2. Install Package Control (https://sublime.wbond.net/installation)
3. Cmd + Shift + P 
4. Type "Install Package" and select "Package Control: Install Package"

``Install npm packages``
1. Cmd + Shift + P
2. Type "npm install" and select
3. insert npm install <package name> to install package
    -npm install
        -install saved packages 
    -npm install <pkg name> --save
        -install and save packages as dependencies
    -npm install <pkg name> --save-dev
        -install and save package as a development dependency
    -npm install <pkg name> --save-optional
        -install and save package as an optional dependency (overrides dependencies if any of they fail, such as rejecting a certain version of a package)

``Install mongoDB``
1. sudo apt-get install -y mongodb-org
2. mkdir mongo_data (inside workspace dir)
3. echo 'mongod --bind_ip=$IP --dbpath=/home/ubuntu/workspace/mongo_data --nojournal --rest "$@"' > run_mongod
4. chmod a+x run_mongod
    -./run_mongod from the console to run the database
5. npm init
6. npm install --save mongodb

``Install Mongoose``
1. npm install express mongoose body-parser --save

``Install Mocha(globally) & Chai``
1. npm install mocha -g chai chai-http --save-dev
2. if it doesnt work, you might have to do a sudo install:
    ` $sudo npm install mocha -g chai chai-http --save-dev`

``Install passport & bcrypt``
1. npm install --save express body-parser mongoose passport passport-http bcryptjs

``Install node.js with express module``
1. npm install --save express
2. echo $C9_HOSTNAME
    -checks for hostname link

``Install react, babel, and webpack``
1. npm install --save-dev mocha chai react-addons-test-utils babel-register
2. npm install --save react react-dom
3. npm install --save-dev babel-preset-react
4. npm install --save-dev webpack
5. npm install --save-dev babel-core babel-preset-es2015 babel-loader
6. npm install --save react-router
6. touch webpack.config.js
```
var path = require('path');

    var webpack = require('webpack');

    var packageData = require('./package.json');

    var filename = [packageData.name, packageData.version, 'js'];

    module.exports = {
        entry: path.resolve(__dirname, packageData.main),
        output: {
            path: path.resolve(__dirname, 'build'),
            filename: filename.join('.'),
        },
        devtool: 'source-map',
        module: {
            loaders: [
                {
                    test: /\.js$/,
                    exclude: /(node_modules)/,
                    loader: 'babel',
                    query: {
                        presets: ['es2015', 'react']
                    }
                }
            ]
        }
    };
```
7. inside package.json
```
    "scripts": {
        //helps us set up mocha and looks for file in folder called test
        "test": "mocha --compilers js:babel-register test/**/*.js*"
      },
      "babel": {
        "presets": ["es2015", "react"]
      }
```

``Install Redux``
1. npm install --save redux

``Install Async Actions``
1. npm install --save redux-thunk
2. add this to store.js
```
var store = createStore(reducers.repositoryReducer, applyMiddleware(thunk));
module.exports  = store;
```

``Install polyfill for HTTP fetch API``
1. npm install --save isomorphic-fetch
2. action.js
```
require('isomorphic-fetch');
```

``REACT CHEATSHEET``
http://tinyurl.com/reactcheatsheet

``REDUX CHEATSHEET``
http://redux.js.org/docs/basics/
http://tinyurl.com/reduxcheatsheet

``cURL Requests``
`GET`
curl http://localhost:8080/items
`POST`
curl -X POST -H "Content-Type: application/json" -d '{"name": "durian"}'
http://localhost:8080/items
`PUT`
curl X PUT -H "Content-Type": application/json -d '{"name": "durian", "id": 3}' http://localhost:8080/items/3
`DELETE`
curl -X DELETE http://localhost:8080/items/3

``HEROKU``
`Login`
$heroku login
Enter your Heroku credentials.
Email: frodo@example.com
Password:
Could not find an existing public key.
Would you like to generate one? [Yn]
Generating new SSH public key.
Uploading ssh public key /Users/frodo/.ssh/id_rsa.pub
`heroku create`
$ heroku create
Creating stark-fog-398... done, stack is cedar
http://stark-fog-398.herokuapp.com/ | git@heroku.com:stark-fog-398.git
Git remote heroku added
$ git push heroku master
`checks if dyno is running to serve the app`
$ heroku ps:scale web=1
Scaling web processes... done, now running 1
`open`
$ heroku open

``Create new repo from bash using github api``
1. curl -u 'INSERT GITHUB USERNAME HERE' https://api.github.com/user/repos -d '{"name":"INSERT REPO NAME HERE","description":"INSERT OPTIONAL DESCRIPTION HERE"}'
    -Example
    curl -u 'Lavioli' https://api.github.com/user/repos -d '{"name":"panda-helper","description":"cheat sheet app made with content up to week 6 in thinkful"}'
should get a list of urls
2. search for "ssh_url" and copy it
    -Example: "ssh_url": "git@github.com:Lavioli/panda-helper.git"
3. git remote add origin git@github.com:Lavioli/panda-helper.git

