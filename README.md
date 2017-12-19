# react-redux-expressjs-azure-example
A Todos web app built with ReactJS and Redux as frontend, which is served by expressJS as backend, and deployed to Microsoft Azure Web App service by GitHub.

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

[TODO: add screenshot]

## Deploy the Express App in Azure

NOTE: this sesson is referenced from [3]

* Step 1: browse Microsoft Azure Portal and sign in:

```
https://portal.azure.com/
```

* Step 2: create an new web app in Azure:

In the dashboard of Azure Portal, create an new web app in the following steps:

```
New > Web + Mobile > Web App
```
[TODO: add screenshot]

Fill in the web app details, including:

```
App name
Subscription
Resource Group
OS
App Service plan/Location
Application Insights
```
[TODO: add screenshot]

Then, hit the create button to create the web app.

Wait for a little bit, then referesh the browser, the web app `react-redux-expressjs-azure-example` appears in the dashboard as App Service. Clicking on `react-redux-expressjs-azure-example` App Service brings up details of the azure app, from where the hosted app can be browsed by `Overview > Browse` with an url of `https://react-redux-expressjs-azure-example.azurewebsites.net`:

[TODO: add screenshot]

* Step 3: deploy the express app to azure

Deployment is done by configuring the deployment options with github repo:

```
DEPLOYMENT > Deployment options > Choose Source > GitHub > Choose project and Choose branch > OK
```

Then, the express web app in GitHub shows up in the `Deployment options` screen and building. Once the building is passed, which looks like:

[TODO: add screenshot]

Browse the azure app, it should show the react app in `https://react-redux-expressjs-azure-example.azurewebsites.net`:

[TODO: add screenshot]

After this step, any change in the `master` branch triggers a new deployment in Azure.

## [TODO] Add the React and Redux TODO-List App to the Express App

* Step 1. Create react and redux TODO list app

First, create a `client` folder in the root folder to host the redux code.

Then, add the Redux Todos Example [4] to the `client` rolder.

Then, add modules for the redux todos app:

in root folder:

```
cd client
npm install
```

Browse the redux todos app:

```
npm start
```

Type `http://localhost:3000` in local browser, the redux todos app shows up:

[TODO: add screenshot]

* Step 2. Serve the React and Redux Todos App by the Express App

The react and redux todos app is serverd by pointing the express app's frontend to the production build of the react and redux app.

First, build the react and redux app with the following command in the `client` directory, which generates a `build/` folder:

```
npm run build
```

Then, configure `app.js` in the root folder to serve the react and redux app by replacing line 23 (`app.use(express.static(path.join(__dirname, 'public')));`) with:

```
app.use(express.static(path.join(__dirname, './client/build')));
```

Now the react and redux app should show up in the express port. To test it, in the root directory, run the express app in port `2048`:

```
PORT=2048 node bin/www
```

Then browse the express app in `http://localhost:2048`, the react and redux todos app shows up:

[TODO: add screenshot]

Finally, committing all the changes to `master` branch should deploy the react and redux app in Azure!

[TODO: add screenshot]

## [TODO] Automate the web app deployment in Azure


## Reference

[1] Create React App with an Express Backend: https://daveceddia.com/create-react-app-express-backend/

[2] Express Application Generator: https://expressjs.com/en/starter/generator.html

[3] Create a Node.js web app in Azure: https://docs.microsoft.com/en-us/azure/app-service/app-service-web-get-started-nodejs

[4] Redux Todos example: https://github.com/reactjs/redux/tree/master/examples/todos
