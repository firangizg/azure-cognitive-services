# 3. Create and consume Cognitive Services

### Introduction

Azure Cognitive Services are cloud-based services that encapsulate AI Capabilities, and includes services such as:

- Language, Translator
- Speech
- Computer Vision, Custom Vision, Face
- Anomaly Detector, Content Moderator, Personalizer

Cognitive Services underpin Azure Applied AI Services that provide out-of-the-box solutions for common AI scenarios. Some examples of AI services:

- Azure Form Recognizer
    - an optical character recognition (OCR) solution
    - can extract semantic meaning from forms (invoice, receipts)
- Azure Metrics Advisor
    - built on Anomaly Detector
    - simplifies real-time monitoring and response to critical metrics
- Azure Video Analyzer for Media
    - video anlaysts solution built on Video Indexer service
- Azure Immersive Reader
    - reading solution supporting people of all ages and abilities
- Azure Bot Services
    - cloud service for delivering conversational AI solutions or bots
- Azure Cognitive Search
    - cloud-scale search solution that uses cognitive services to extract insights from data and documents

### Provision a cognitive services resource

To use any of the cognitive services, you need to create appropriate resources in an Azure subscription to define an endpoint where the services can be consumed, provide access keys for authenticated access and to manage billing for your app’s usage of the service. 

Options for resources:

- Multi-service
    - You can create a single resource that enables you to use Language, Comp Vision, Speech and other services
    - Enables you to manage a single set of access credentials to consume mult services at a single endpoint, and with a single point of billing for usage of all services
- Single-service
    - Create discrete Lang and Comp Vision resources
    - Enables you to use separate endpoints for each service and manage access credentials independently.
    - Generally offers a free tier

Most cognitive servicees can be used through a single Azure services, some offer separate resources for model training and prediction. Enables you to manage billing for training custom models separately from model consumption by applications and in most cases allows you to use dedicated service-specific resource to train a model, but a generic resource to make the model available for inferencing. 

### **Identify endpoints and keys**

When you provision a cognitive service resource in your Azure subscription, you are defining an endpoint through which the service can be consumed by an app. To consume the service through the endpoint, apps require the following info:

- The Endpoint URI: http address at which REST interface can be accessed. Most SDKs use the endpoint URI to initate a connection to the endpoint
- Subscription Key: when you provision a cognitive services resource, 2 keys are created - applications can use either key. you can also regenerate them as required to control access
- Resource location: when you provision a resource, you assign it to a location which determines Azure data center in which the resource is defined. most SDKs use the endpoint URI to connect to the service, some require the location

### Use a REST API

Cognitive services provide REST APIs that client apps can use to consume services. Most cases, service funcs can be called by submitting data in JSON format over an HTTP request (may be POST, PUT, or GET). The results are returned to the client as an HTTP response, often w JSON contents that encapsulate the output data from the function. 

The use of REST interfaces w an HTTP endpoint means that any prog lang or tool capable of submitting and receiving JSON over HTTP can be used to consume cognitive services. 

### Use an SDK

You can develop app that uses cognitive services using REST interfaces, but it’s easier to create more complex solutions by using native libraries for the prog lang. SDKs for commong prog langs abstract the REST interfaces for most cognitive service. Each SDK includes packages that you can install in order to use service-specific libraries in your code and online doc to help you determine the appropriate classes, methods and parameters used to work with the service. 

### **Exercise - Use Cognitive Services**

In this example, you'll explore a console application that uses the **Language** REST API to perform language detection

Knowledge checkpoint: 

- **How are client applications typically granted access to a cognitive services endpoint?**
    - The application must specify a valid subscription key for the Azure resource.
- **In which format are message exchanged between a client app and a cognitive services resource when using a REST API?**
    - JSON
