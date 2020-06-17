# Node-RED Dashboards and UI Techniques 
Dashboards are incredibly useful in a variety of industries. They provide incredible visual insight into applications functionalities and are a great way to measure metrics, visualize data, get alerted with updates and drill down into important details all in one place. Creating effective dashboards for your API driven applications can get pretty tricky and might require a lot of effort and front-end development knowledge. However, Node-RED’s UI nodes makes it effective and easy for anyone to create informative visualizations and within minutes! 

In this lab we will be walking through various different things you can make using Node-RED dashboards! 

![Image1](/Labs/Images/db3.png)

## Contents 
1. Prerequisits 
2. Lab 
3. References 

## Prerequisites
To complete this tutorial, you need an [IBM Cloud account](https://cloud.ibm.com/login?cm_sp=ibmdev-_-developer-tutorials-_-cloudreg) (IBM Cloud Lite, trial, or paid account).

Please go through [Get Started with Node-RED on IBM Cloud](https://github.com/pmmistry/Node-RED-Series#get-started-with-node-red-on-ibm-cloud) to get an instance of Node-RED running on IBM Cloud. 

###  Installing `node-red-dashboard` nodes
In this lab we are going to be building useer interfaces using [Node-RED Dashboard Nodes](https://flows.nodered.org/node/node-red-dashboard) 

The Node-RED Dashboard nodes provide a very intuitive and effective way to mock up user interfaces for event driven applications. 

First thing that you will need to get started is to install `node-red-dashboard` nodes into your Node-RED Editor. 

To do this you will need to 
1. Go to manage palette in your Node-RED Editor 

![Image2](/Labs/Images/db10.png)

2. Find `node-red-dashboard` in install tab 

![Image3](/Labs/Images/db7.png)

3. Install Dashboard Nodes and see them in your Node-RED Editor palette under dashboard 

![Image4](/Labs/Images/db11.png) 


## Lab 
We will be creating 3 different kinds of dashboards in this lab 
-  Basic Dashboard 
-  CPU Dashboard 
-  Space Station Dashboard  

## Basic Dashboard 
In this flow we will learn the basics of dashboard nodes and build a UI dashboard with buttons, alerts, gauges, sliders, line charts and bar charts. 
By the end of this tutorial your dashboard should look like this : 
![Img2](/Labs/Images/db2.png)

### Step 1 .  Drag a Button Node and Configure Groups and Tabs 
Drag a Button node out into the pallet and double click to edit this button's properties. 

![Img12](/Labs/Images/db12.png)

The label describes the button's name and when clicked the button is sending the current time stamp.  Double click on the pencil button next to the group field and indicate the group's name and which tab this field belongs to. In my case I called the tab Demo and the group a button. This tab and group will be used once you add more UI elements to the page. 

![Img13](/Labs/Images/db13.png)

Click update and done when you are done editing this UI element.  You will notice your Tab and group name on the right hand in the layout tab . You can add tabs and groups here as well. 

![Img14](/Labs/Images/db14.png)

Connect a debug node to this button node and then deploy.  To see how the dashboard looks like  click on the little square with upward arrow to see the dashboard in another webpage tab. You should see a button and when you click on it you should see current timestamp in your debug console in node -RED .

![Img15](/Labs/Images/db15.png)
![Img16](/Labs/Images/db16.png)

### Step 2. Adding a text box that corresponds to the button 

Drag a Text Node and connect it to output of button node  

![Img17](/Labs/Images/db17.png)
![Img18](/Labs/Images/db18.png)

Make sure that the group and tab for the text node are same as the group and tab for the button. This ensures that the text box will correspond to the button UI element . Click deploy and refresh dashboard web page and you should see : 

![Img19](/Labs/Images/db19.png)

### Step 3. Add an Alert 

Drag a notification node to the workspace and connect it with the output of the button node 

![Img20](/Labs/Images/db20.png)

Edit Notification Node's Layout 

![Img21](/Labs/Images/db21.png)

Now once you click the button you should see an alert with the time stamp 

### Step 4. Add Audio Output 

Connect Audio Out  Node to Button Output 

![Img22](/Labs/Images/db22.png)

Make sure audio out is the same tag and group as the button element

![Img23](/Labs/Images/db23.png)

Audio Out only takes text and converts it into audio. So change timestamp input from the button node to string . 

![Img23](/Labs/Images/db24.png)

Deploy , and when you click on the button on the dashboard you should hear audio output. 

### Step 5 . Create another group on the same Tab 

This other group will be called Analog and it will be on the same dashboard web page but it will include a slider, a gauge , a line chart and a bar chart ! 

![Img25](/Labs/Images/db25.png)

Drag slider node and connect its output to gauge node , chart node \(line\) , and chart node \(bar\). 

![Img26](/Labs/Images/db26.png)

Make sure all nodes are part of Analog group and set range from 0 - 200 

#### Slider: 
![Img26](/Labs/Images/db27.png)

#### Guage: 

![Img26](/Labs/Images/db28.png)

#### Chart: 
![Img26](/Labs/Images/db29.png)


Deploy all changes and open dashboard UI. You should see gauge, line and bar chart fluctuate based on slider input. 
 
### To import Basic Dashboard flow go to : [textAnalyzer.flow](/Labs/Flows/basicDashboard.flow)