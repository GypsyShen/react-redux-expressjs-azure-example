# react-redux-expressjs-azure-example
A TODO list web app built with React and Redux as frontend, which is served by expressJS, and is deployed in Microsoft Azure Web App service.

## Create the Express App

NOTE: this section is referenced from [1].

* Step 1: install the express-generator [2] utility:

```
$ npm install -g express-generator
```

* Step 2: create the Express app:

In the root folder of the project, run:

```
$ express react-backend
```

The command generates two items to the root folder:

```
LICENSE
react-backend/
```

* Step 3: move react-backend files to root folder

Moving react-backend files to the root folder makes it simpler to host the web app in Azure, because Azure would directly take express app files in root folder of the project and connect it to its hosting service. But it is doable to not moving the files and configure project files in Azure for deployment.

Now the root folder should contain the following items:

```
app.js
bin/
LICENSE
package.json
public/
routes/
views/
```

* Step 4: run the Express app locally

In root folder:

First, install the modules by the following command:

```
npm install
```

Second, run the app by the following command:

```
PORT=3001 node bin/www
```

Third, browse the Express app by the following URL in a browser:

```
http://localhost:3001
```

It should looks like:



## [TODO] Deploy express app in Azure

## [TODO] Create react and redux TODO list app

## [TODO] Serve react and redux TODO list app

## [TODO] Automate the web app deployment in Azure


## Reference

[1] Create React App with an Express Backend: https://daveceddia.com/create-react-app-express-backend/

[2] Express Application Generator: https://expressjs.com/en/starter/generator.html

