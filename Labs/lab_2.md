# Node-RED Dashboards and UI Techniques 
Dashboards are incredibly useful in a variety of industries. They provide incredible visual insight into applications functionalities and are a great way to measure metrics, visualize data, get alerted with updates and drill down into important details all in one place. Creating effective dashboards for your API driven applications can get pretty tricky and might require a lot of effort and front-end development knowledge. However, Node-RED’s UI nodes makes it effective and easy for anyone to create informative visualizations and within minutes! 

In this lab we will be walking through various different things you can make using Node-RED dashboards! 

![Image1](/Labs/Images/db3.png)

## Contents 
1. [Prerequisits](https://github.com/pmmistry/Node-RED-Series/blob/master/Labs/lab_2.md#prerequisites)
    - [Installing node-red-dashboard nodes](https://github.com/pmmistry/Node-RED-Series/blob/master/Labs/lab_2.md#installing-node-red-dashboard-nodes)
2. [Labs](https://github.com/pmmistry/Node-RED-Series/blob/master/Labs/lab_2.md#lab)
3. [Basic Dashboard](https://github.com/pmmistry/Node-RED-Series/blob/master/Labs/lab_2.md#basic-dashboard)
    - [Import Basic Dashboard](https://github.com/pmmistry/Node-RED-Series/blob/master/Labs/lab_2.md#to-import-basic-dashboard-flow-go-to--basicdashboardflow)
4. [CPU Dashboard](https://github.com/pmmistry/Node-RED-Series/blob/master/Labs/lab_2.md#cpu-dashboard) 
    - [Import CPU Dashboard](https://github.com/pmmistry/Node-RED-Series/blob/master/Labs/lab_2.md#to-import-cpu-dashboard-flow-go-to--cpudashboardflow)
5. [Space Station](https://github.com/pmmistry/Node-RED-Series/blob/master/Labs/lab_2.md#space-station)
    - [Import Space Station Dashboard](https://github.com/pmmistry/Node-RED-Series/blob/master/Labs/lab_2.md#to-import-space-station-dashboard-flow-go-to--spacestationdashboardflow)
   

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
 
### To import Basic Dashboard flow go to : [BasicDashboard.flow](/Labs/Flows/basicDashboard.flow)

```
[{"id":"9583b8de.96bc48","type":"tab","label":"Basic Dashboard Elements","disabled":false,"info":""},{"id":"fd446b54.5da24","type":"ui_button","z":"9583b8de.96bc48","name":"","group":"2fb9c205.dae50e","order":2,"width":0,"height":0,"passthru":false,"label":"click me","tooltip":"","color":"","bgcolor":"","icon":"","payload":"Hi This is a Demo","payloadType":"str","topic":"","x":170,"y":200,"wires":[["9569387b.fc24f","103477f0.45b588","b7e35051.2b75b","3375341f.88f7e4"]]},{"id
":"103477f0.45b588","type":"ui_text","z":"9583b8de.96bc48","group":"2fb9c205.dae50e","order":1,"width":0,"height":0,"name":"","label":"Click Here !","format":"","layout":"row-spread","x":370,"y":140,"wires":[]},{"id":"9569387b.fc24f","type":"debug","z":"9583b8de.96bc48","name":"","active":true,"tosidebar":true,"console":false,"tostatus":false,"complete":"payload","targetType":"msg","x":390,"y":200,"wires":[]},{"id":"3692c3e.596783c","type":"ui_gauge","z":"9583b8de.96bc48","name":"","group":"122a9c51.bdf31c","order":1,"width":0,"height":0,"gtype":"gage","title":"gauge","label":"units","format":"","min":0,"max":"200","colors":["#00b500","#e6e600","#ca3838"],"seg1":"75","seg2":"150","x":390,"y":420,"wires":[]},{"id":"b5c97926.f8f0e","type":"ui_slider","z":"9583b8de.96bc48","name":"","label":"slider","tooltip":"","group":"122a9c51.bdf31c","order":1,"width":0,"height":0,"passthru":true,"outs":"all","topic":"","min":0,"max":"200","step":1,"x":150,"y":420,"wires":[["3692c3e.596783c","be838f3e.6af14","da3a316d.a4e43"]]},{"id":"be838f3e.6af14","type":"ui_chart","z":"9583b8de.96bc48","name":"","group":"122a9c51.bdf31c","order":3,"width":"0","height":"0","label":"line chart","chartType":"line","legend":"false","xformat":"HH:mm:ss","interpolate":"linear","nodata":"","dot":false,"ymin":"0","ymax":"200","removeOlder":"2","removeOlderPoints":"","removeOlderUnit":"60","cutout":0,"useOneColor":false,"colors":["#1f77b4","#aec7e8","#ff7f0e","#2ca02c","#98df8a","#d62728","#ff9896","#9467bd","#c5b0d5"],"useOldStyle":false,"outputs":1,"x":380,"y":500,"wires":[[]]},{"id":"da3a316d.a4e43","type":"ui_chart","z":"9583b8de.96bc48","name":"","group":"122a9c51.bdf31c","order":4,"width":"0","height":"0","label":"bar chart","chartType":"bar","legend":"false","xformat":"HH:mm:ss","interpolate":"linear","nodata":"","dot":false,"ymin":"0","ymax":"200","removeOlder":1,"removeOlderPoints":"","removeOlderUnit":"3600","cutout":0,"useOneColor":false,"colors":["#1f77b4","#aec7e8","#ff7f0e","#2ca02c","#98df8a","#d62728","#ff9896","#9467bd","#c5b0d5"],"useOldStyle":false,"outputs":1,"x":380,"y":560,"wires":[[]]},{"id":"b7e35051.2b75b","type":"ui_toast","z":"9583b8de.96bc48","position":"top right","displayTime":"3","highlight":"","outputs":0,"ok":"OK","cancel":"","topic":"","name":"","x":370,"y":280,"wires":[]},{"id":"3375341f.88f7e4","type":"ui_audio","z":"9583b8de.96bc48","name":"","group":"2fb9c205.dae50e","voice":"en-US","always":"","x":360,"y":60,"wires":[]},{"id":"2fb9c205.dae50e","type":"ui_group","z":"","name":"Button","tab":"de296677.584f4","order":1,"disp":true,"width":"6","collapse":false},{"id":"122a9c51.bdf31c","type":"ui_group","z":"","name":"Analog","tab":"de296677.584f4","order":2,"disp":true,"width":"6","collapse":false},{"id":"de296677.584f4","type":"ui_tab","z":"","name":"Demo","icon":"dashboard","order":3,"disabled":false,"hidden":false}]
```


## CPU Dashboard 
This flow will monitor and create alerts for CPU usage. In this flow you will learn how to install the CPU usage node and create a UI dashboard that sends alerts when CPU usage is greater than 50%. By the end of this tutorial your dashboard should look like this : 
![Img2](/Labs/Images/db0.png)

### Step 1. Connect timestamp input to dashboard switch node 

![Img2](/Labs/Images/db30.png)

Drag input node and set input properties to send time stamps. Connect input node to switch dashboard node. Create a new tab and group for dashboard node. This way all dashboards can be found in a hamburger menu all in one web page. 

![Img2](/Labs/Images/db31.png)

Connect switch dashboard node to switch function node and set msg.payload  is true in switch properties to indicate on switch 

### Step 2. Install CPU usage node 

Go to manage palette and install  `node-red-contrib-cpu` 

![Img2](/Labs/Images/db9.png)

Once installed drag CPU node and set property to : 

![Img](/Labs/Images/db32.png)

Connect CPU node to debug node to see message for each core usage on debug panel. Connect CPU node output to chart dashboard to chart a line graph of messages from CPU. Connect a switch node and a notificiation node to alert when messages for CPU cores are greater than 50% 

![Img](/Labs/Images/db33.png)

For chart node make sure to create a new group under CPU tab 

![Img](/Labs/Images/db34.png)

Use a template node between a switch node and alert node to create a template for the message you want to alert : 

![Img](/Labs/Images/db35.png)

### Step 3. Create a gauge for each core 

![Img](/Labs/Images/db36.png)

Use switch node to seperate data coming from all 4 cores. Create seperate guages to map for each core's data. 

![Img](/Labs/Images/db38.png)

Make sure you create a separate group for the gauges . In my case the Tab is still CPU but the group is CPU guages . In the end the dashboard is all under one tab - CPU and there are 3 separate groups - CPU on and off , CPU utilization and CPU gauges . 

Flow should look like this : 

![Img](/Labs/Images/db37.png)

Deploy all changes and see dashboard . When switch is turned on , you should see 4 lines on the utilization chart , as well as different values coming in from each gauge. You should see alerts when values are greater than 50. 

### To import CPU Dashboard flow go to : [CPUDashboard.flow](/Labs/Flows/cpuDashboard.flow)

```text
[{"id":"90da6d14.cc65d8","type":"tab","label":"CPU Dashboard","disabled":false,"info":""},{"id":"1e9d7bc0.fcb984","type":"debug","z":"90da6d14.cc65d8","name":"","active":true,"tosidebar":true,"console":false,"tostatus":false,"complete":"payload","targetType":"msg","x":430,"y":140,"wires":[]},{"id":"d274050d.badb88","type":"ui_chart","z":"90da6d14.cc65d8","name":"","group":"baa4830e.d51ff","order":0,"width":"8","height":"6","label":"chart","chartType":"line","legend":"false","xformat":"HH:mm:ss","interpolate":"linear","nodata":"","dot":false,"ymin":"0","ymax":"100","removeOlder":"1","removeOlderPoints":"","removeOlderUnit":"60","cutout":0,"useOneColor":false,"colors":["#1f77b4","#aec7e8","#ff7f0e","#2ca02c","#98df8a","#d62728","#ff9896","#9467bd","#c5b0d5"],"useOldStyle":false,"outputs":1,"x":410,"y":200,"wires":[[]]},{"id":"968d0d83.26b41","type":"inject","z":"90da6d14.cc65d8","name":"","topic":"","payload":"","payloadType":"date","repeat":"1","crontab":"","once":false,"onceDelay":"","x":110,"y":60,"wires":[["4b6874aa.19c8d4"]]},{"id":"4b6874aa.19c8d4","type":"ui_switch","z":"90da6d14.cc65d8","name":"","label":"switch","tooltip":"","group":"6d02446b.841c64","order":0,"width":0,"height":0,"passthru":true,"decouple":"false","topic":"","style":"","onvalue":"true","onvalueType":"bool","onicon":"","oncolor":"","offvalue":"false","offvalueType":"bool","officon":"","offcolor":"","x":270,"y":60,"wires":[["7697565f.2e6618"]]},{"id":"7697565f.2e6618","type":"switch","z":"90da6d14.cc65d8","name":"Switch On","property":"payload","propertyType":"msg","rules":[{"t":"true"}],"checkall":"true","repair":false,"outputs":1,"x":420,"y":60,"wires":[["ed89ea38.72527"]]},{"id":"f12ff5fc.0fc79","type":"ui_toast","z":"90da6d14.cc65d8","position":"top right","displayTime":"3","highlight":"","outputs":0,"ok":"OK","cancel":"","topic":"","name":"","x":690,"y":260,"wires":[]},{"id":"2b2616b0.28443a","type":"template","z":"90da6d14.cc65d8","name":"Alert","field":"payload","fieldType":"msg","format":"handlebars","syntax":"mustache","template":"Alert: CPU {{topic}} is {{payload}}%","output":"str","x":530,"y":260,"wires":[["f12ff5fc.0fc79"]]},{"id":"3af072a3.14a1ce","type":"switch","z":"90da6d14.cc65d8","name":"","property":"payload","propertyType":"msg","rules":[{"t":"gt","v":"50","vt":"num"}],"checkall":"true","repair":false,"outputs":1,"x":410,"y":260,"wires":[["2b2616b0.28443a"]]},{"id":"36c7bd83.27b4f2","type":"ui_gauge","z":"90da6d14.cc65d8","name":"","group":"3d630fa8.8d0d68","order":0,"width":"0","height":"0","gtype":"gage","title":"CPU 1","label":"units","format":"{{value}}","min":0,"max":"100","colors":["#00b500","#e6e600","#ca3838"],"seg1":"","seg2":"","x":590,"y":320,"wires":[]},{"id":"29073f22.c591c8","type":"switch","z":"90da6d14.cc65d8","name":"","property":"topic","propertyType":"msg","rules":[{"t":"eq","v":"core_1","vt":"str"},{"t":"eq","v":"core_2","vt":"str"},{"t":"eq","v":"core_3","vt":"str"},{"t":"eq","v":"core_4","vt":"str"}],"checkall":"true","repair":false,"outputs":4,"x":410,"y":380,"wires":[["36c7bd83.27b4f2"],["b3ee09cd.598f48"],["1ab8d355.16ca75"],["8bd46bad.a915f"]]},{"id":"b3ee09cd.598f48","type":"ui_gauge","z":"90da6d14.cc65d8","name":"","group":"3d630fa8.8d0d68","order":0,"width":0,"height":0,"gtype":"gage","title":"CPU 2","label":"units","format":"{{value}}","min":0,"max":"100","colors":["#00b500","#e6e600","#ca3838"],"seg1":"","seg2":"","x":590,"y":360,"wires":[]},{"id":"1ab8d355.16ca75","type":"ui_gauge","z":"90da6d14.cc65d8","name":"","group":"3d630fa8.8d0d68","order":0,"width":0,"height":0,"gtype":"gage","title":"CPU 3","label":"units","format":"{{value}}","min":0,"max":"100","colors":["#00b500","#e6e600","#ca3838"],"seg1":"","seg2":"","x":590,"y":400,"wires":[]},{"id":"8bd46bad.a915f","type":"ui_gauge","z":"90da6d14.cc65d8","name":"","group":"3d630fa8.8d0d68","order":0,"width":0,"height":0,"gtype":"gage","title":"CPU 4","label":"units","format":"{{value}}","min":0,"max":"100","colors":["#00b500","#e6e600","#ca3838"],"seg1":"","seg2":"","x":590,"y":440,"wires":[]},{"id":"ed89ea38.72527","type":"cpu","z":"90da6d14.cc65d8","name":"","msgCore":true,"msgOverall":false,"msgArray":false,"msgTemp":false,"x":210,"y":200,"wires":[["1e9d7bc0.fcb984","d274050d.badb88","3af072a3.14a1ce","29073f22.c591c8"]]},{"id":"baa4830e.d51ff","type":"ui_group","z":"","name":"CPU Utilitization","tab":"262952a9.f1dcbe","order":2,"disp":true,"width":"8"},{"id":"6d02446b.841c64","type":"ui_group","z":"","name":"CPU On/Off","tab":"262952a9.f1dcbe","order":1,"disp":true,"width":"3"},{"id":"3d630fa8.8d0d68","type":"ui_group","z":"","name":"CPU Gauges","tab":"262952a9.f1dcbe","order":3,"disp":true,"width":"3"},{"id":"262952a9.f1dcbe","type":"ui_tab","z":"","name":"CPU","icon":"dashboard","order":9}]
```


## Space Station 
This flow uses the template node to embed a Map. It then embeds the tracks of the exact location of the International Space Station onto the map.

![Img](/Labs/Images/db39.png)

This flow uses the template dashboard node to embed a world map. Then it uses the world map nodes to plot tracks of the ISS location. To see this flow in action install `node-red-contrib-web-worldmap` nodes in manage pallet.

![Img](/Labs/Images/db8.png)

Once flow is created it should look like : 
![Img](/Labs/Images/db1.png)

### To import Space Station Dashboard flow go to : [spaceStationDashboard.flow](/Labs/Flows/spaceStation.flow)

```text
[{"id":"2e17c6be.73371a","type":"tab","label":"Space Station","disabled":false,"info":""},{"id":"ef4cb1a.87258d","type":"inject","z":"2e17c6be.73371a","name":"Every 5 sec","topic":"","payload":"","payloadType":"date","repeat":"5","crontab":"","once":false,"onceDelay":"","x":130,"y":180,"wires":[["5740ee56.e02b9"]]},{"id":"431abcaa.a86a4c","type":"http request","z":"2e17c6be.73371a","name":"","method":"GET","ret":"obj","paytoqs":false,"url":"http://api.open-notify.org/iss-now.json","tls":"","proxy":"","authType":"","x":610,"y":180,"wires":[["a0b54275.fdffa","88797856.1dede8"]]},{"id":"a0b54275.fdffa","type":"debug","z":"2e17c6be.73371a","name":"","active":true,"tosidebar":true,"console":false,"tostatus":false,"complete":"payload","targetType":"msg","x":790,"y":240,"wires":[]},{"id":"88797856.1dede8","type":"function","z":"2e17c6be.73371a","name":"Extract ISS Location","func":"var iss_location = msg.payload.iss_position;\n\nmsg.payload = { \n        name : \"International Space Station\",\n        lat  : parseFloat(iss_location.latitude),\n        lon  : parseFloat(iss_location.longitude),\n//        icon:\"uav\",\n        icon: \"fa-space-shuttle\",\n        iconColor:'#900000',\n        command : { \"zoom\" : 5 }\n};\n\nreturn msg;","outputs":1,"noerr":0,"x":820,"y":180,"wires":[["2c4edb22.0e8b7c","ce09ee81.f288b","d9bb1570.f3c058"]]},{"id":"2c4edb22.0e8b7c","type":"debug","z":"2e17c6be.73371a","name":"","active":true,"tosidebar":true,"console":false,"tostatus":false,"complete":"payload","targetType":"msg","x":1030,"y":240,"wires":[]},{"id":"347e393a.d67736","type":"ui_template","z":"2e17c6be.73371a","group":"d20c8bbb.c142b8","name":"Embedded Map","order":0,"width":"20","height":"15","format":"<div ng-bind-html=\"msg.payload | trusted\"></div>","storeOutMessages":true,"fwdInMessages":true,"templateScope":"local","x":780,"y":100,"wires":[[]]},{"id":"a728c35a.c1429","type":"template","z":"2e17c6be.73371a","name":"Add Map to Dashboard","field":"payload","fieldType":"msg","format":"handlebars","syntax":"mustache","template":"<iframe src={{{payload.url}}} height=750px width=1000px ></iframe>","x":550,"y":100,"wires":[["347e393a.d67736"]]},{"id":"d720d4e.7019e28","type":"comment","z":"2e17c6be.73371a","name":"One time - Add Map to Dashboard","info":"","x":180,"y":60,"wires":[]},{"id":"9479465b.ea08c8","type":"inject","z":"2e17c6be.73371a","name":"Init WorldMap","topic":"","payload":"true","payloadType":"bool","repeat":"","crontab":"","once":true,"onceDelay":"","x":130,"y":100,"wires":[["ad2c3d03.9a2be"]]},{"id":"ad2c3d03.9a2be","type":"function","z":"2e17c6be.73371a","name":"Inject /worldmap","func":"msg.payload =   {\n                url : \"/worldmap\",\n              \n                };\nreturn msg;","outputs":1,"noerr":0,"x":320,"y":100,"wires":[["a728c35a.c1429"]]},{"id":"854255a9.3272a8","type":"comment","z":"2e17c6be.73371a","name":"Query the location of the International Space Station","info":"","x":234.44444444444446,"y":144.44444444444443,"wires":[]},{"id":"5740ee56.e02b9","type":"ui_switch","z":"2e17c6be.73371a","name":"","label":"switch","tooltip":"","group":"8ba82d7d.d6815","order":0,"width":0,"height":0,"passthru":true,"decouple":"false","topic":"","style":"","onvalue":"true","onvalueType":"bool","onicon":"","oncolor":"","offvalue":"false","offvalueType":"bool","officon":"","offcolor":"","x":290,"y":180,"wires":[["5e151b68.97cb6c"]]},{"id":"5e151b68.97cb6c","type":"switch","z":"2e17c6be.73371a","name":"Switch On","property":"payload","propertyType":"msg","rules":[{"t":"true"}],"checkall":"true","repair":false,"outputs":1,"x":440,"y":180,"wires":[["431abcaa.a86a4c"]]},{"id":"ce09ee81.f288b","type":"worldmap","z":"2e17c6be.73371a","name":"","lat":"","lon":"","zoom":"5","layer":"Esri Satellite","cluster":"","maxage":"","usermenu":"show","panit":"true","hiderightclick":"false","coords":"none","path":"","x":1070,"y":180,"wires":[]},{"id":"d9bb1570.f3c058","type":"worldmap-tracks","z":"2e17c6be.73371a","name":"","depth":"20","layer":"combined","x":950,"y":120,"wires":[["ce09ee81.f288b"]]},{"id":"d20c8bbb.c142b8","type":"ui_group","z":"2e17c6be.73371a","name":"Space Station","tab":"d79763ec.17455","order":2,"disp":true,"width":"20","collapse":false},{"id":"8ba82d7d.d6815","type":"ui_group","z":"","name":"Start/Stop","tab":"d79763ec.17455","order":1,"disp":true,"width":"3","collapse":false},{"id":"d79763ec.17455","type":"ui_tab","z":"2e17c6be.73371a","name":"International Space Station Location ","icon":"fa-space-shuttle","order":10,"disabled":false,"hidden":false}]
```