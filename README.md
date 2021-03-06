# [Ghost](https://github.com/TryGhost/Ghost/) on [IBM Bluemix](https://www.bluemix.net)

Ghost is a very popular blogging platform, it's built by [Ghost Foundation](https://ghost.org/) on Node.js and a selection of SQL solutions.

## Deploying to [IBM Bluemix](https://www.bluemix.net)

> **Note:** This will provision a MySQL instance within Bluemix which may incur costs, please see [here](https://console.ng.bluemix.net/catalog/services/compose-for-mysql/) for more information

### The easy way
The easiest way to deploy this app to [IBM Bluemix](https://www.bluemix.net) using [Compose](https://github.com/compose) for MySQL is to deploy via the button below.
[![Deploy to Bluemix](https://deployment-tracker.mybluemix.net/stats/abefe890d326502f6d7382fb2a7fb381/button.svg)](https://bluemix.net/deploy?repository=https://github.com/ibm-cds-labs/ghost-on-bluemix.git)

### Manual installation

To manually install this app to [IBM Bluemix](https://www.bluemix.net) via the command line you will need either the `bluemix` or `cf` command line tool. The instructions for installing this can be found at [http://clis.ng.bluemix.net/ui/home.html] and [https://github.com/cloudfoundry/cli/releases] respectively.

Once you have these tools, you will need to assign a [IBM Bluemix](https://www.bluemix.net) API to the tool. The command is:

`cf api <api url>`

The available API URLs currently are `https://api.ng.bluemix.net` (US), `https://api.eu-gb.bluemix.net` (UK) and `https://api.au-syd.bluemix.net` (AUS). Once you have assigned an API endpoint you will need to login via

`cf login`

Once that's done we can actually deploy the app. First you will need to grab your own copy.

```
git clone git@github.com:ibm-cds-labs/ghost-on-bluemix.git
cd ghost-on-bluemix
```

You will also need to create the instance of [Compose](https://github.com/compose) for MySQL using the command:

`cf create-service compose-for-mysql Standard GhostDatabase`

Once the instance is created all you need to do is deploy the code to [IBM Bluemix](https://www.bluemix.net) with the command:

`cf push`

Now you have a working version of [Ghost](https://github.com/TryGhost/Ghost/) running on [IBM Bluemix](https://www.bluemix.net).

## Setting up your administrator

Once you have a working version of [Ghost](https://github.com/TryGhost/Ghost/) you will need to create an Admin user to start creating posts and managing the blog. You will need to go to your application on [IBM Bluemix](https://www.bluemix.net) with the following path `<route to applitions>/ghost/setup` and follow the on screen prompts.

## Disabling Deployment Tracking

For manual deploys, deployment tracking can be disabled by removing require("cf-deployment-tracker-client").track(); from the end of the `index.js` main server file.

## License

Copyright 2017 IBM Watson Data Platform

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0
Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.
