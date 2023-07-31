# 6. Deploy cognitive services in containers

Containers enable you to host Azure Cognitive Servicees either on-premises or on Azure. Deploying Cognitive Services in a container on-premises will decrease latency btw service and local data, which can improve performance. 

### Understand containers

When you deploy software service, it must be hosted in an env that provides hardware, OS, and supporting runtime components. 

- Azure Cognitive Services is provided as a cloud service, in which the service software is hosted in an Azure data center.
- You can also deploy it in a container, which encapsulates necessary runtime components and in turn is deployed in a container host that provides the underlying OS and hardware.

> Container comprises an application/serice and runtime components needed to run it, while abstracting the underlying OS and hardware. Two significant benefits:
> 
1. Containers are portable across hosts, which may run diff OS or use diff hardware, making it easier to move an app and all its dependencies
2. A single container host can support multiple isolated contianers, each w its own specific runtime config - making it easier to consolidate mult apps that have diff config requirements

A container is encapsulated in a container image that defines the software and config it must support. 

- Images can be stored in a central registry like Docker Hub or you can maintain a set of images in your own registry.

To use a container, you pull the container image from a registry and deploy it to a container host, specifying any required config settings. Container host can be in the cloud, private network or local computer. (A Docker server, an Azure Container Instance (ACI) or Azure Kubernetes Service (AKS) cluster). 

To learn more about containers: [https://learn.microsoft.com/en-us/training/modules/intro-to-docker-containers/](https://learn.microsoft.com/en-us/training/modules/intro-to-docker-containers/) 

### Use Cognitive Services containers

There are container images for Azure Cognitive Services in the Microsoft Container Registry that you can use to deploy containerized service that encapsulates individual cognitive service API

To deploy + use cogntivie services container:

1. container image for specific Cognitive Services API must be downloaded and deployed to a container host like local Docker server, ACI or AKS
2. client apps must submit data to the endpoint provided by the containerized service and retrieve results just as they would from cognitive services cloud resource in Azure
3. usage metrics for containerized service are sent to a cognitive services resource in Azure to calculate billing

Even when usign a container, you must provision a cognitive services resource in Azure for billing purposes. Client apps send requests to the containerized service, so sensitive data’s not sent to the resource endpoint in Azure, but container must be able to connect to the Cognitive Services resource in Azure periodically to send usage metrics for billing. 

Each container has subset of cognitive services functionality. For example:

- Not all features of Language service are in a single container
- Language detection, translation, and sentiment analysis are each separate container images, but the setup steps are similar.
- For Lang service, each of the 3 core features maps to a separate image:
    
    
    | Key Phrase Extraction | mcr.microsoft.com/azure-cognitive-services/textanalytics/keyphrase |
    | --- | --- |
    | Language Detection | mcr.microsoft.com/azure-cognitive-services/textanalytics/language |
    | Sentiment Analysis v3 (English) | mcr.microsoft.com/azure-cognitive-services/textanalytics/sentiment:3.0-en |
- You can use Docker pull command to downlaod container images to work with them directly from your machine. Some containers are in a “Gated” public preview state, so you need to explicitly request access, otherwise they are available to use w Azure deployment.

When you deploy Cognitive Services container image to ahost, you need to specify 3 settings:

- ApiKey: key from deployed Azure Cognitive Service
- Billing: endpoint URI from deployed Azure Cognitive Service
- Eula: value of accept to state you accept the license for the container

After container is deployed, apps consume the containerized Cognitive Services endpoint rather than default Azure endpoint. Client app must be configured w the appropriate endpoint but doesn’t need to provide subscription key to be authenticated. You can implement ur own authentication solution and apply network security restrictions as appropriate for your specific app scenario. 

### Knowledge Check

**1. You plan to use a cognitive services container in a local Docker host. Which of the following statements is true?**

- Client applications must pass a subscription key to the Azure resource endpoint before using the container.
- The container must be able to connect to the Azure resource endpoint to send usage data for billing.
- All data passed from the client application to the container is forwarded to the Azure resource endpoint.

**2. Which of the following parameters must you specify when deploying a Cognitive Services container image?**

- EULA
- ResourceGroup
- SubscriptionName

**3. You plan to use the language detection functionality of the Language cognitive service in a container. Which container image should you deploy?**

- mcr.microsoft.com/azure-cognitive-services/textanalytics
- mcr.microsoft.com/azure-cognitive-services
- mcr.microsoft.com/azure-cognitive-services/textanalytics/language