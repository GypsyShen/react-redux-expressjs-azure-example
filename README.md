# react-redux-expressjs-azure-example
A TODO list web app built with React and Redux as frontend, which is served by expressJS, and is deployed in Microsoft Azure Web App service by GitHub.

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

[TODO] It should looks like:

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

## [TODO] Create react and redux TODO list app

## [TODO] Serve react and redux TODO list app

## [TODO] Automate the web app deployment in Azure


## Reference

[1] Create React App with an Express Backend: https://daveceddia.com/create-react-app-express-backend/

[2] Express Application Generator: https://expressjs.com/en/starter/generator.html

[3] Create a Node.js web app in Azure: https://docs.microsoft.com/en-us/azure/app-service/app-service-web-get-started-nodejs
