# Node-RED Essentials 
In this lab you will learn how to build a text analyzer using Node-RED essentials techniques. We will be using drag and drop nodes with Watson APIs to analyze and gain useful insights. We be using services such as tone analyzer, text to speech , audio output , language translator and twitter data source. 

## Contents
1. [Prerequisites](#prerequisites)
2. [Lab](#lab)
    - [Step 1](https://github.com/pmmistry/Node-RED-Series/blob/master/Labs/lab_1.md#step--1--connecting-inject-nodes-to-tone-analyzer-service)
    - [Step 2](https://github.com/pmmistry/Node-RED-Series/blob/master/Labs/lab_1.md#step--2--set-score-to-tone) 
    - [Step 3](https://github.com/pmmistry/Node-RED-Series/blob/master/Labs/lab_1.md#step-3--add-language-translator--text-to-speech-and-audio-output-nodes)
    - [Step 4](https://github.com/pmmistry/Node-RED-Series/blob/master/Labs/lab_1.md#optional-step-4--connect-to-twitter)
3. [ Get the Code](https://github.com/pmmistry/Node-RED-Series/blob/master/Labs/lab_1.md#get-the-code)

4. [References](#references)


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

### To use watson nodes you will need to create Watson Service on IBM Cloud
Steps : 
1. [Go to IBM Cloud Catalog](https://github.com/pmmistry/Node-RED-Series#step-1-find-the-node-red-starter-in-the-ibm-cloud-catalog)
2. Search for service you want to use 
3. Create Lite Service 
4. Once service is created you can reference `Service Credentials` for each service to use in Node-RED nodes 

![Image0](/Labs/Images/nr0.png)

## Lab 
In this lab we are going to create a text analyzer. Optionally you could turn this text analyzer into a tweet analyzer using twitter social nodes. We will be using tone analyzer service, language translator and speech to text in this tutorial. 

Lets get started! 

### Step  1 : Connecting Inject Nodes to Tone Analyzer Service 
1. Drag three inject nodes and name each node `Happy test` , `Sad test` and `Angry test` 

2.  Double click on inject node and set property as  **payload**
   -  For Happy test set payload to  `{"text":"every one is awesome"}` 
   -  For Sad test set payload to `{"text":"This is miserable and sad"}`
   -  For Angry test set payload to `{"text":"I hate this demo"}`
    
 ![Image2](/Labs/Images/nr2.png) 

   > **Note**: This text is suppose to symbolize a tweet. Feel free to add your own text example .


3. Drag a tone analyzer node from IBM Watson Nodes in the palette and connect to all three text nodes. 

4. [Create a tone analyzer service from IBM Cloud](https://github.com/pmmistry/Node-RED-Series/blob/master/Labs/lab_1.md#to-use-watson-nodes-you-will-need-to-initiate-watson-service-on-ibm-cloud) and add `API Key` and `Service Endpoint` to tone analyzer node. 
 ![Image3](/Labs/Images/nr3.png)

5. Add debug node and change node to end of tone analyzer node : 

  Debug Node Settings 
  - Name node `Print msg.response` to see response of tone analyzer 
  - Set output to `msg.response` 
  Change Node Settings 
  - Name node `tone_categories`
  - Set `msg.payload` to  `msg.response.document_tone.tone_categories` to get tone category result 
  - Connect a debug node called `Tone categories` to end of change node  
 ![Image4](/Labs/Images/nr4.png)

6. Click on Deploy button and test by injecting text 
 ![Image5](/Labs/Images/nr5.png)



### Step  2 : Set Score to Tone 

1. Insert function node and name node `High Score`. Connect Node to Tone Analyzer Service and add the code below to filter out emotions from Tone analyzer service and give a score value . 
 - Add a debug node at end of `High Score` function node 

    ```var emotions = [];
    emotions = msg.response.document_tone.tone_categories
                    .filter(function(c){
                        if (c.category_id == "emotion_tone")
                        {return c; }
                        })[0].tones;

    var myscore =  0;
    for (var i=0; i<emotions.length; i++) {
        if(emotions[i].score > myscore) {
            msg.payload = emotions[i].score;
            msg.topic = emotions[i].tone_name;
            myscore = emotions[i].score;
        }
    }
    return msg;
    ```
![Image6](/Labs/Images/nr6.png)
![Image7](/Labs/Images/nr7.png)

2. Insert Switch to select for emotions. You will be adding emotions `Joy`, `Sadness` ,`Fear`,`Anger`and`Disgust` 
    - Connect switch node to `High Score Function Node`  
    - Connect each emotion to a template node calld `Score tweet` 
    -  `Score tweet` includes payload : 
        ```This tweet expresses {{topic}} - {{tweet.text}}```

    See screenshots for setup : 
![Image8](/Labs/Images/nr8.png)

3. Deploy and test 
![Image12](/Labs/Images/nr12.png)

### Step 3 : Add language translator , text to speech and audio output nodes 
1. Go to  IBM cloud and create language translator and text to speech services. 
2. Connect language translator node to end of `Score Tweet` payload and add in service credentials 
3. Connect language translator to text to speech node . Add service credentials for text to speech . 
4. Connect a change node and set `msg.payload` to `msg.speech` 
5. Install audio node by : Going to hamburger menu > Manage palette > install > search `node-red-contrib-play-audio` 
6. Deploy and test 
![Image13](/Labs/Images/nr13.png)

### Optional Step 4 : Connect to twitter 
1. Search and install `node-red-node-twitter` in Manage palette. Once installed create the following flow : 

![Image14](/Labs/Images/nr14.png)

2. To use twitter node you will need twitter ID and twitter API credentials . Set up your twitter credentials at : [https://developer.twitter.com/en/apps](https://developer.twitter.com/en/apps)


3. Once you have your twitter node set up , connect your twitter flow to tone analyze service and test. 

    Your flow should look like : 
![Image16](/Labs/Images/nr16.png)

## Get the Code

**Importing:**
An alternative to creating a flow is importing a flow. You can import a flow fairly easily by going to hamburger menu > Import > Pasting json you would like to import

**Exporting:** 
Similarly if you want to share your flows you can also export your flows by going to hamburger menu > Export > Download 

### To import text analyzer flow go to : [textAnalyzer.flow](/Labs/Flows/textAnalyzer.flow)

### To import tweet analyzer flow go to : [tweetAnalyzer.flow](/Labs/Flows/tweetAnalyzer.flow)

## References

