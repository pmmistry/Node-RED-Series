# Node-RED Series
Node-RED is a wonderful flow based programming tool that makes it easy to make event driven applications in a simple and intuitive way. Node-RED is a low code programming environment for beginners and experts alike who want to write and understand programming flow.

Node-RED provides plugins called nodes which can be installed to support almost everything related to programming. It can be used for APIs, DataBase, IoT devices, WebSockets, Emails, Scripting, Image Processing, Cloud computing, edge computing, creating websites and lot more one can think of doing it based on NodeJS. In this workshop we will go over getting started  with Node-RED on [IBM Cloud](https://cloud.ibm.com/login?cm_sp=ibmdev-_-developer-tutorials-_-cloudreg) and learning Node-RED essentials.

## Contents

1. [Get Started with Node-RED on IBM Cloud](https://github.com/pmmistry/Node-RED-Series#get-started-with-node-red-on-ibm-cloud)
    - [Step 1:Find the Node-RED Starter in the IBM Cloud catalog](https://github.com/pmmistry/Node-RED-Series#step-1-find-the-node-red-starter-in-the-ibm-cloud-catalog)
    - [Step 2: Create your application](https://github.com/pmmistry/Node-RED-Series#step-2-create-your-application)
    - [Step 3: Enable the Continuous Delivery feature](https://github.com/pmmistry/Node-RED-Series#step-3-enable-the-continuous-delivery-feature)
    - [Step 4: Open the Node-RED application](https://github.com/pmmistry/Node-RED-Series#step-4-open-the-node-red-application)
    - [Step 5:Configure your Node-RED application](https://github.com/pmmistry/Node-RED-Series#step-5configure-your-node-red-application)
2. [Labs](https://github.com/pmmistry/Node-RED-Series#labs)
3. [References]


## Get Started with Node-RED on IBM Cloud 
In this tutorial, you will learn how to create a Node-RED starter application in the IBM Cloud, including a Cloudant database to store the application flow configuration.

### Prerequisites 
To complete this tutorial, you need an [IBM Cloud account](https://cloud.ibm.com/login?cm_sp=ibmdev-_-developer-tutorials-_-cloudreg) (IBM Cloud Lite, trial, or paid account).

### Estimated Time 
You can complete this tutorial in less than 20 minutes.

### Step 1: Find the Node-RED Starter in the IBM Cloud catalog 
1. Log in to [IBM Cloud](https://cloud.ibm.com/login?cm_sp=ibmdev-_-developer-tutorials-_-cloudreg).
2. Open the catalog and search for **node-red**.
3. Click on the **Node-RED App** tile.

 ![Image1](/Images/img1.png)

 ### Step 2: Create your application
 Now you need to create the Node-RED Starter application.
 1. On the Create tab, a randomly generated App name will be suggested. Either accept that default name or provide a unique name for your application. This will become part of the application URL.

 Note: If the name is not unique, you will see an error message and you must enter a different name before you can continue.

2. The Node-RED Starter application requires an instance of the Cloudant database service to store your application flow configuration. Select the region the service should be created in and what pricing plan it should use.

Note: You can only have one Cloudant instance using the Lite plan. If you have already got an instance, you will be able to select it from the Pricing plan select box. You can have more than one Node-RED Starter application using the same Cloudant service instance.

3. Click the Create button to continue. This will create your application, but it is not yet deployed to IBM Cloud.

![Image2](/Images/img2.png)

### Step 3: Enable the Continuous Delivery feature
At this point, you have created the application and the resources it requires, but you have not deployed it anywhere to run. This step shows how to setup the Continuous Delivery feature that will deploy your application into the Cloud Foundry space of IBM Cloud.

1. On the next screen, click the **Deploy your app** button to enable the Continuous Delivery feature for your application.
![Image3](/Images/img3.png)

2. You will need to create an IBM Cloud API key to allow the deployment process to access your resources. Click the **New** button to create the key. 
![Image4](/Images/img4.png)

A message dialog will appear. You can accept the default values and confirm to close the dialog.
![Image5](/Images/img5.png)

3. Increase the Memory allocation per instance slider to at least 128MB. If you do not increase the memory allocation, your Node-RED application might not have sufficient memory to run successfully.

4. The Node-RED Starter kit only supports deployment to the Cloud Foundry space of IBM Cloud. Select the region to deploy your application to. This should match the region you created your Cloudant instance in. Lite users might only be able to deploy to your default region.

![Image6](/Images/img6.png)

Click **Next** to continue.

5. Configure the DevOps toolchain by selecting the region it should be created in – again, try to match the region you selected previously. 

![Image7](/Images/img7.png)

Click **Create**. This will take you back to the application details page.

6. After a few moments, the **Deployment Automation** section will refresh with the details of your newly created Delivery Pipeline. The Status field of the pipeline will eventually show **In progress**. That means your application is being built and deployed.

Click on the **Status** field to see the full status of the Delivery Pipeline.

![Image8](/Images/img8.png)

7. The Deploy stage will take a few minutes to complete. You can click on the **View logs and history** link to check its progress. Eventually the Deploy stage will go green to show it has passed. This means your Node-RED Starter application is now running.

![Image9](/Images/img9.png)

### Step 4: Open the Node-RED application
Now that you’ve deployed your Node-RED application, let’s open it up!

1. Back on the application details page, you should now see the **App URL**, **Source** and **Deployment** target fields filled in.

![Image10](/Images/img10.png)

2. Click on the **App URL** to open up your Node-RED application in a new browser tab.

### Step 5:Configure your Node-RED application
The first time you open your Node-RED app, you’ll need to configure it and set up security.

1. A new browser tab will open with the Node-RED start page.
![Image11](/Images/img11.png)

2. On the initial screen, click **Next** to continue.

3. Secure your Node-RED editor by providing a **username** and **password**. If you need to change these at any point, you can either edit the values in the Cloudant database, or override them using environment variables. The documentation on nodered.org describes how to do this. Click Next to continue.
![Image12](/Images/img12.png)

4. The final screen summarizes the options you’ve made and highlights the environment variables you can use to change the options in the future. Click Finish to proceed.

5. Node-RED will save your changes and then load the main application. From here you can click the Go to your Node-RED flow editor button to open the editor.

![Image13](/Images/img13.png)

The Node-RED editor opens showing the default flow.

![Image14](/Images/img14.png)


## Labs 
 After you have finished creating a Node-RED instance on IBM Cloud you can go through these labs to build some Node-RED Applications

* [Lab 1 : Node-RED Essentials](/Labs/lab_1.md) 
* [Lab 2 : Node-RED UI and Dashboard Techniques](/Labs/lab_2.md)
* [Lab 3 : Node-RED End to End App](/Labs/lab_3.md) 

## References 
- [Create a Node-RED starter application](https://developer.ibm.com/tutorials/how-to-create-a-node-red-starter-application/)
- [Node-RED IBM Developer Docs](https://developer.ibm.com/components/node-red/)
- [Getting Started with Node-RED](https://nodered.org/docs/getting-started/)
- [Node-RED Flows](https://nodered.org/docs/getting-started/)
