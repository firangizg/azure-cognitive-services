# 1. Get started w AI on Azure

### Intro to AI

AI is the creation of software that imitates human behaviors and capabilities.

- **Machine learning** - This is often the foundation for an AI system, and is the way we "teach" a computer model to make predictions and draw conclusions from data.
- **Anomaly detection** - The capability to automatically detect errors or unusual activity in a system.
- **Computer vision** - The capability of software to interpret the world visually through cameras, video, and images.
- **Natural language processing** - The capability for a computer to interpret written or spoken language, and respond in kind.
- **Knowledge mining** - The capability to extract information from large volumes of often unstructured data to create a searchable knowledge store.

### Understand ML

Microsoft Azure provides the **Azure Machine Learning** service - a cloud-based platform for creating, managing, and publishing machine learning models. Azure Machine Learning provides the following features and capabilities:

| Feature | Capability |
| --- | --- |
| Automated machine learning | This feature enables non-experts to quickly create an effective machine learning model from data. |
| Azure Machine Learning designer | A graphical interface enabling no-code development of machine learning solutions. |
| Data and compute management | Cloud-based data storage and compute resources that professional data scientists can use to run data experiment code at scale. |
| Pipelines | Data scientists, software engineers, and IT operations professionals can define pipelines to orchestrate model training, deployment, and management tasks. |

### **Understand anomaly detection**

*Anomaly detection* - a machine learning based technique that analyzes data over time and identifies unusual changes.

In Azure, the **Anomaly Detector** service provides an application programming interface (API) that developers can use to create anomaly detection solutions: [Anomaly Detector service web site](https://azure.microsoft.com/services/cognitive-services/anomaly-detector/).

### **Understand computer vision**

Most computer vision solutions are based on ML models that can be applied to visual input from cameras, videos, or images. The following table describes common computer vision tasks.

| Feature | Capability |
| --- | --- |
| Image classification | Train a ML model to classify images based on their contents. Ex: in a traffic monitoring solution you might use an image classification model to classify images based on the type of vehicle they contain, such as taxis, buses, cyclists, and etc. |
| Object detection | Trained to classify individual objects within an image, and identify their location with a bounding box. Ex: a traffic monitoring solution might use object detection to identify the location of different classes of vehicle. |
| Semantic segmentation | Advanced ML technique where individual pixels are classified according to object they belong. Ex: a traffic monitoring solution might overlay traffic images with "mask" layers to highlight different vehicles using specific colors. |
| Image analysis | Data scientists, software engineers, and IT operations professionals can define pipelines to orchestrate model training, deployment, and management tasks. |
| Face detection, analysis, and recognition | Specialized form of object detection that locates human faces in an image. This can be combined with classification and facial geometry analysis techniques to recognize individuals based on their facial features. |
| Optical character recognition (OCR) | Technique used to detect and read text in images. You can use OCR to read text in photographs (for example, road signs or store fronts) or to extract information from scanned documents such as letters, invoices, or forms. |

*Things Azure offers:*

| Service | Capabilities |
| --- | --- |
| Computer Vision | You can use this service to analyze images and video, and extract descriptions, tags, objects, and text. |
| Custom Vision | Use this service to train custom image classification and object detection models using your own images. |
| Face | The Face service enables you to build face detection and facial recognition solutions. |
| Form Recognizer | Use this service to extract information from scanned forms and invoices. |

### **Understand NLP**

Natural language processing (NLP) is the area of AI that deals with creating software that understands written and spoken language. Enables software that can:

- Analyze and interpret text in documents, email messages, and other sources.
- Interpret spoken language, and synthesize speech responses.
- Automatically translate spoken or written phrases between languages.
- Interpret commands and determine appropriate actions.

*Things Azure offers:*

| Service | Capabilities |
| --- | --- |
| Language | Use this service to access features for understanding and analyzing text, training language models that can understand spoken or text-based commands, and building intelligent applications. |
| Translator | Use this service to translate text between more than 60 languages. |
| Speech | Use this service to recognize and synthesize speech, and to translate spoken languages. |
| Azure Bot | This service provides a platform for conversational AI, the capability of a software "agent" to participate in a conversation. Developers can use the Bot Framework to create a bot and manage it with Azure Bot Service - integrating back-end services like Language, and connecting to channels for web chat, email, Microsoft Teams, and others. |

### **Knowledge mining**

Term used to describe solutions that involve extracting information from large volumes of often unstructured data to create a searchable knowledge store.

**Azure Cognitive Search** is a private, enterprise, search solution that has tools for building indexes

### **Challenges and risks of AI**

| Challenge or Risk | Example |
| --- | --- |
| Bias can affect results | A loan-approval model discriminates by gender due to bias in the data with which it was trained |
| Errors may cause harm | An autonomous vehicle experiences a system failure and causes a collision |
| Data could be exposed | A medical diagnostic bot is trained using sensitive patient data, which is stored insecurely |
| Solutions may not work for everyone | A home automation assistant provides no audio output for visually impaired users |
| Users must trust a complex system | An AI-based financial tool makes investment recommendations - what are they based on? |
| Who's liable for AI-driven decisions? | An innocent person is convicted of a crime based on evidence from facial recognition – who's responsible? |

### **Understand responsible AI**

1. Fairness
    1. suppose you create a machine learning model to support a loan approval application for a bank. The model should predict whether the loan should be approved or denied without bias. This bias could be based on gender, ethnicity, or other factors that result in an unfair advantage or disadvantage to specific groups of applicants.
    2. Azure ML includes the capability to interpret models and quantify the extent to which each feature of the data influences the model's prediction. This capability helps data scientists and developers identify and mitigate bias in the model.
2. Reliability and safety
    1. consider an AI-based software system for an autonomous vehicle; or a machine learning model that diagnoses patient symptoms and recommends prescriptions. Unreliability in these kinds of systems can result in substantial risk to human life.
    2. must be subjected to rigorous testing and deployment management processes to ensure that they work as expected before release.
3. Privacy and security
    1. The machine learning models on which AI systems are based rely on large volumes of data, which may contain personal details that must be kept private. Even after the models are trained and the system is in production, privacy and security need to be considered. As the system uses new data to make predictions or take action, both the data and decisions made from the data may be subject to privacy or security concerns.
4. Inclusiveness
    1. AI systems should empower everyone and engage people. AI should bring benefits to all parts of society, regardless of physical ability, gender, sexual orientation, ethnicity, or other factors.
5. Transparency
    1. Users should be made fully aware of the purpose of the system, how it works, and what limitations may be expected.
6. Accountability
    1. Designers and developers of AI-based solutions should work within a framework of governance and organizational principles that ensure the solution meets ethical and legal standards that are clearly defined.

For more resources to help you put the responsible AI principles into practice, see [https://www.microsoft.com/ai/responsible-ai-resources](https://www.microsoft.com/ai/responsible-ai-resources).

To see these policies in action you can read about [Microsoft’s framework for building AI systems responsibly](https://blogs.microsoft.com/on-the-issues/2022/06/21/microsofts-framework-for-building-ai-systems-responsibly/).
