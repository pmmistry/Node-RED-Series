# Node-RED: Build a COVID-19 dashboard

Use The Weather Company Disease Tracker API to easily access disease data

![COVID-19 Dashboard](https://raw.githubusercontent.com/Call-for-Code/node-red-contrib-twc-covid19-tracker/master/screenshots/Node-RED-COVID19-StateCounty-Dashboard.png)

## Build a Node-RED COVID-19 dashboard

The Weather Company unveiled a new disease tracker API for Call for Code developers that aggregrates COVID-19 data from trusted primary sources and tracks where the coronavirus is spreading over time. With this API, developers can create solutions to inform local, state, and county officials as they plan shelter-in-place guidelines and show citizens how adhering to those restrictions has a positive impact in slowing COVID-19 disease progression. Tracking where the coronavirus (COVID-19) is spreading is an important measure in fighting against the virus.

The disease tracker API is exclusively available to developers who are participating in the 2020 [Call for Code Global Challenge](https://developer.ibm.com/callforcode/blogs/developer.ibm.com/callforcode) and building solutions to fight the impact of COVID-19. Developers who have accepted the challenge can [register](https://callforcode.weather.com/register) and receive a time-limited API key.

In addition to powering [the weather.com COVID statistics](https://weather.com/coronavirus/l/40.75,-73.99) page, The Weather Company created the disease tracker API to provide active disease metrics including confirmed cases, deaths, and recoveries over a historical period of up to 60 days in the past. All the data is fully attributed to the primary sources, such as the U.S. Centers for Disease Control and Prevention and state and county health departments, allowing for trust in AI, which is critical for accurate decision making.

In this tutorial, shows you how to access COVID-19 location and infection data through an API provided by The Weather Company (TWC) and incorporate that data into Node-RED dashboard, charts, and tables. Use Node-RED for data analysis and data visualization of COVID-19 infections by country, state, and county.

### Learning objectives

In this tutorial, you will:
- Install Node-RED in IBM Cloud
- Learn about Node-RED
- Explore the node-red-contrib-twc-covid19-tracker Node-RED node
- Experiment with node-red-dashboard charts and node-red-node-ui-table tables
- Build a Call for Code COVID-19 Disease Tracking Dashboard using TWC Disease Tracker API

## Create a Node-RED Starter application

In prior Node-RED Series workshops, we created a Node-RED Starter Application running in IBM Cloud.  If you haven't created one, follow these [instructions](https://developer.ibm.com/components/node-red/tutorials/how-to-create-a-node-red-starter-application/)

## Register for a Weather Company API key

You need an API key to use The Weather Company API for COVID-19 Disease Tracking.  [Call for Code](https://developer.ibm.com/callforcode) participants can read the Terms of Service, register to join the [Call for Code 2020 COVID Challenge](https://developer.ibm.com/callforcode/getstarted/covid-19/) and request a TWC API key for this Node-RED node at [callforcode.weather.com](https://callforcode.weather.com) A time-limited API key will be sent to you via email.

## Learn about Node-RED

[Node-RED](http://nodered.org) is an open source programming tool for wiring together hardware devices, APIs, and online services in new and interesting ways. It provides a browser-based editor that makes it easy to wire together flows using the wide range of nodes in the palette that can be deployed to its runtime in a single-click.

![Node-RED Example](https://raw.githubusercontent.com/node-red/node-red.github.io/master/images/node-red-screenshot-sm.png)

## Install Node-RED dependencies nodes

After Node-RED is installed, this tutorial requires you to add some additional dependencies:

* [node-red-contrib-twc-covid19-tracker](https://flows.nodered.org/node/node-red-contrib-twc-covid19-tracker)
* [node-red-node-ui-table](https://flows.nodered.org/node/node-red-node-ui-table)
* [node-red-dashboard](https://flows.nodered.org/node/node-red-dashboard)

##  Review the TWC Disease Tracker API documentation

The Weather Company offers [TWC Weather Data Packages](https://business.weather.com/products/weather-data-packages) that are available for purchase. The Node-RED node in this package implements the Disease Tracking API service and is free for Call for Code participants (please review the [Terms of Service](https://callforcode.weather.com/register/))

The TWC Disease Tracker API allows you to track the progression of the COVID-19 disease for a given location. It provides information regarding active diseases including confirmed cases, deaths, and recoveries over a period of up to 60 days in the past.

Review the [online documentation](https://weather.com/swagger-docs/ui/sun/v3/sunV3DiseaseTracker.json) for more information about The Weather Company API for Disease Tracking.

Review the [online documentation](https://weather.com/swagger-docs/ui/sun/v3/sunV3DiseaseTrackerCountryList.json) for more information about The Weather Company API for Global Disease Country Reporting.

The APIs returns an array of json objects containing COVID-19 data which you can integrate into dashboards or applications.

## Explore the node-red-contrib-twc-covid19-tracker Node-RED node

This Node-RED package creates **twc covid19 tracker** and **twc covid19 country report** nodes in your Node-RED palette.  It wraps the TWC Disease tracker API so that it is easier to incorporate the API into your Node-RED flows.

- **twc covid19 tracker** - Query 60 day history of COVID-19 statistics at the Country, State, County level by Geocode, Place ID or Postal Code.
- **twc covid19 country report** - Query the current state of a disease for a set of countries globally.

Once the node is installed in your Node-RED palette, drag it to your flow and double-click on the **twc covid tracker** node. In the **Properties** dialog box, enter the following information:

* Your TWC API Key provided by [callforcode.weather.com](https://callforcode.weather.com)
* Specify whether the node will retrieve **Country**, **State**, or **County** COVID-19 data
* Specify the location you are interested in: **geocode** (latitude/longitude), **place ID**, or **postal key**
* The location either via latitude/longitude, place id, or postal code. Examples:
  * 40.74,-73.99
  * 327145917e06d09373dd2760425a88622a62d248fd97550eb4883737d8d1173b
  * 10001:US

Review the node information documentation in the Node-RED right hand side bar for techniques that allow you to programmatically pass in the above parameters via a `msg.twcparams` json object.

![node-red-contrib-twc-covid19-tracker node properties](https://raw.githubusercontent.com/Call-for-Code/node-red-contrib-twc-covid19-tracker/master/screenshots/node-red-contrib-twc-covid19-tracker-nodeproperties.png)

## Node-RED charts and tables

The **node-red-dashboard** package provides a variety of UI elements in the Node-RED palette that you can use to construct a dashboard. These gauges, charts, sliders, drop down lists, entryfields, and buttons can be wired to build informative dashboards with very little code.

The **node-red-node-ui-table** package provides a table element in the Node-RED palette that you can use to construct robust tabular data.

## Node-RED COVID-19 statistics dashboards

These nodes will be wired to build a COVID-19 Data Dashboard that visualizes Country (US) and State data in a chart and in a table.
Now that you know a little about Node-RED, Dashboard and Table nodes, the TWC Disease Tracker API and the node-red-contrib-twc-covid19-tracker node, we can start to assemble these components to implement a Node-RED COVID-19 statistics dashboard.

Access COVID-19 location and infection data through an API provided by **The Weather Company** (TWC) and incorporate that data in
Node-RED dashboard, charts, and tables. Once we've created these dashboards, we can start to use Node-RED for data analysis and data visualization of COVID-19 infections
by country, state and county.

The [node-red-contrib-twc-covid19-tracker GitHub repository](https://github.com/call-for-code/node-red-contrib-twc-covid19-tracker) includes a collection of Node-RED Dashboard examples that display COVID-19 statistics.

Three examples are provided in a GitHub [examples](https://github.com/call-for-code/node-red-contrib-twc-covid19-tracker/tree/master/examples) folder.

In the following steps you will learn how to implement Node-RED COVID-19 statistics dashboards using The Weather Company Disease Tracker API using these examples.

## Learn how to Import Examples

### Import a prebuilt flow from GitHub

Since configuring Node-RED nodes and wiring them together requires many steps to document in screenshots, there is an easier way to build a flow by importing a prebuilt flow into your application.

* Some of the upcoming steps will have a **Get the Code** link.

* When instructed, open the **Get the Code** github URL, mark or Ctrl-A to select all of the text, and copy the text for the flow to your Clipboard.
* Click on the Node-RED Menu **(6)**, then Import **(7)**, then Clipboard **(8)**.
![IBM Cloud Node-RED Starter screenshot](https://raw.githubusercontent.com/IBM/IoT-AssetTracking-Perishable-Network-Blockchain/master/Node-RED/screenshots/IBMCloud-NodeRED-import.png)
* Paste the text of the flow into the **Import nodes** dialog and press the red **Import** button.
![IBM Cloud Node-RED Starter screenshot](https://raw.githubusercontent.com/IBM/IoT-AssetTracking-Perishable-Network-Blockchain/master/Node-RED/screenshots/IBMCloud-NodeRED-pastefromclipboard.png)
* The new flow will be imported into a new tab in the Node-RED Editor.

## Test the TWC COVID-19 API endpoints

Test each of the TWC COVID-19 APIs by importing this [covid19-api-test.json](https://github.com/call-for-code/node-red-contrib-twc-covid19-tracker/blob/master/examples/covid19-api-test.json) flow.

![COVID API Test Example](https://raw.githubusercontent.com/Call-for-Code/node-red-contrib-twc-covid19-tracker/master/screenshots/Node-RED-TWC-COVID-api-test-flow.png)

Double click on the **TWC API Key** Change node and paste in your Weather Company API key that arrived via email.

To deploy the Node-RED flows, click the red **Deploy** button from your UI.

Click on the blue Inject nodes to test the Disease Tracker api endpoints.

The first section retrieves the Country level details using latitude / longitude coordinates, placeid and Postal Code. The second and third sections retrieve the state and county level details. The last section retrieves all country statistics.

Observe the json response results in the Node-RED Debug sidebar.

## Deploy a COVID-19 Disease Tracking Dashboard

The second example builds a Node-RED Dashboard that displays 60 days of USA State COVID-19 historical data in a table and on a chart.

Import this [Node-RED-covid19-dashboard.json](https://github.com/call-for-code/node-red-contrib-twc-covid19-tracker/blob/master/examples/Node-RED-covid19-dashboard.json) flow.

![COVID-19 Dashboard](https://raw.githubusercontent.com/Call-for-Code/node-red-contrib-twc-covid19-tracker/master/screenshots/Node-RED-COVID19-Dashboard-flow.png)

To deploy the Node-RED flows, click the red **Deploy** from your UI.

Open the **Node-RED UI**

![Node-RED COVID-19 Dashboard](https://raw.githubusercontent.com/Call-for-Code/node-red-contrib-twc-covid19-tracker/master/screenshots/Node-RED-COVID19-Dashboard.png)

If you do not see a table of states, turn to the Node-RED tab again and press the blue **Load Table of States**

# County 7 Day Moving Average Dashboard

The final example Node-RED Dashboard displays all of the counties in the State of New Jersey in a table and plots 60 days of COVID-19 historical data on a chart.  It also plots a chart of new cases reported each day and a seven day moving average that demonstrates flattening the curve.

Import this [Node-RED-covid19-county-dashboard.json](https://github.com/call-for-code/node-red-contrib-twc-covid19-tracker/blob/master/examples/Node-RED-covid19-county-dashboard.json) flow.

![COVID-19 Dashboard](https://raw.githubusercontent.com/Call-for-Code/node-red-contrib-twc-covid19-tracker/master/screenshots/Node-RED-COVID19-StateCounty-Dashboard-flow.png)

To deploy the Node-RED flows, click the red **Deploy** button.

![COVID-19 Dashboard](https://raw.githubusercontent.com/Call-for-Code/node-red-contrib-twc-covid19-tracker/master/screenshots/Node-RED-COVID19-StateCounty-Dashboard.png)


## Build your own COVID-19 Disease Tracking Dashboard

Congratulations!

Now that you have completed this tutorial, you are ready to modify these example flows and create your own Node-RED Dashboard to build a COVID data visualization solution. As a possible enhancement, you could add a map that displays infection hotspots or allow your user to enter, select, or display specific country information.

You can contact the author, [John Walicki](https://github.com/johnwalicki/) and provide [feedback](https://github.com/call-for-code/node-red-contrib-twc-covid19-tracker/issues) if you have suggestions on how to improve this tutorial.

# Tutorial Summary

You have now completed the **Node-RED: Build a COVID-19 dashboard** workshop.  I hope you enjoyed working through the various sections building up to the final solution.

Hopefully you now have a good understanding of some of the work needed to create a COVID data analysis dashboard.  In this scenario you:

- Installed Node-RED in IBM Cloud
- Requested an API Key for The Weather Company Disease Tracker API
- Learned about event driven flow programming and Node-RED
- Reviewed the TWC Disease Tracker API swagger / OpenAPI docs
- Explored the node-red-contrib-twc-covid19-tracker Node-RED nodes
- Experimented with Node-RED charts and tables
- Imported several example dashboard flows
- Tested the TWC COVID-19 API endpoints
- Deployed several COVID-19 Tracking Dashboards
- Calculated a Seven Day moving average
- Plotted disease data in Node-RED dashboard charts
