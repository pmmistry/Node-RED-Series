# Node-RED Essentials 
In this lab you will learn how to build a text analyzer using Node-RED essentials techniques. We will be using drag and drop nodes with Watson APIs to analyze and gain useful insights. We be using services such as tone analyzer, text to speech , audio output , language translator and twitter data source.  

## Prerequisites
To complete this tutorial, you need an [IBM Cloud account](https://cloud.ibm.com/login?cm_sp=ibmdev-_-developer-tutorials-_-cloudreg) (IBM Cloud Lite, trial, or paid account).

Please go through [Get Started with Node-RED on IBM Cloud](https://github.com/pmmistry/Node-RED-Series#get-started-with-node-red-on-ibm-cloud) to get an instance of Node-RED running on IBM Cloud
 
### Node-RED Essentials 
![Image1](/Labs/Images/nr1.png)

The [Node-RED Essentials video series](https://www.youtube.com/playlist?list=PLyNBB9VCLmo1hyO-4fIZ08gqFcXBkHy-6) introduces you to the components and features of this low-code editor.

From creating your first flow, to wiring nodes together, to using the sidebar, to managing messages, you can quickly learn Node-RED fundamental skills in these 3 to 4 minute videos.

### Explore node-red-node-watson Node-RED nodes
The [node-red-node-watson GitHub repository](https://github.com/watson-developer-cloud/node-red-node-watson) includes a collection of Node-RED nodes for IBM Watson services.  This package adds the following nodes to your Node-RED palette:

- Assistant: Add conversational capabilities into applications
- Discovery: List environments created for Watson Discovery
- Language Identification: Detect the language used in text
- Language Translator: Translate text from one language to another
- Natural Language Classifier: Use machine learning algorithms to return the top matching predefined classes for short text inputs
- Natural Language Understanding: Analyze text to extract meta-data from content such as concepts, entities, and keywords
- Personality Insights: Use linguistic analytics to infer cognitive and social characteristics from text
- Speech To Text: Convert audio containing speech to text
- Text To Speech: Convert text to audio speech
- Tone Analyzer: Discover, understand, and revise the language tones in text
- Visual Recognition: Analyze visual appearance of images to understand their contents

#### To use watson nodes you will need to initiate Watson Service on IBM Cloud. 
Steps : 
1. [Go to IBM Cloud Catalog](https://github.com/pmmistry/Node-RED-Series#step-1-find-the-node-red-starter-in-the-ibm-cloud-catalog)
2. Search for service you want to use 
3. Create Lite Service 
4. Once service is created you can reference `Service Credentials` for each service to use in Node-RED nodes 

![Image0](/Labs/Images/nr0.png)

## Lab 
In this lab we are going to create a text analyzer. Optionally you could turn this text analyzer into a tweet analyzer using twitter social nodes. We will be using tone analyzer service, language translator and speech to text in this tutorial. 

Lets get started! 

#### Step  1 : Connecting Inject Nodes to Tone Analyzer Service 
1. Drag three inject nodes and name each node `Happy test` , `Sad test` and `Angry test` 
2.  Double click on inject node and set property as  **payload**
   -  For Happy test set payload to  `{"text":"every one is awesome"}` 
   -  For Sad test set payload to `{"text":"This is miserable and sad"}`
   -  For Angry test set payload to `{"text":"I hate this demo"}` 

   > **Note**: This text is suppose to symbolize a tweet. Feel free to add your own text example .
![Image2](/Labs/Images/nr2.png)

3. Drag a tone analyzer node from IBM Watson Nodes in the palette and connect to all three text nodes . 







