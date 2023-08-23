# 14.  Explore Cognitive Services for Vision (preview)

### What’s Microsoft’s Florence foundation model?

- **Image Analysis 4.0**
    - Powered by Microsoft's Florence model.
    - Uses universal visual-lang reps from billions of text-image pairs.
    - Tasks: classification, retrieval, object detection, captioning.
- **Few-shot learning**
    - Predicts using limited sample images.
    - Mirrors human ability to recognize from few samples.
- **Training dataset requirements**
    - Traditionally: massive datasets needed.
    - Microsoft's Custom Vision Service: Min. 15 images.
    - With Florence: Min. just 4 images.
- **Benefits for developers**
    - Efficient computer vision apps.
    - Link data with natural language.
    - Extract insights from visual content.
    - Detail extraction from visual features.

## Analyze images w Azure Computer Vision Image Analysis 4.0

- **Azure Computer Vision Image Analysis 4.0**
    - Purpose: Extract visual elements from images
    - Draws from >10,000 concepts & objects
    - Tasks: Detect, classify, caption, generate insights
    - Powered by: Microsoft's Florence foundation model
    - Uses: Find people in image, categorize image content, describe image with English sentence
- **Access & Usage**
    - Available through: Vision SDK & REST APIs
    - Provides: Advanced AI for image analysis & extracting visual info
- **Describe & Caption Images**
    - Caption features:
        - Caption
            - Generates single sentence describing img, evaluting content holistically
        - Dense Captions
            - provide supplementary info by generating descriptive phrases for individual objects within the image
    - Technology: Florence-based AI models
    - Function: Analyze images, generate human-readable English descriptions
- **Natural Language Image Search**
    - Searches photos based on image/text similarity.
    - Traditional techniques: Use content labels, tags, descriptors.
    - **Image Retrieval in Image Analysis 4.0**
        - Utilizes vectorization: Converts images to multi-dimensional vector space.
        - Vector similarity search: Matches images based on semantic closeness.
        - Benefits: More accurate search results.
        - Allows search with natural language queries without manual tags.
        - Relevant APIs: **`VectorizeImage`** & **`VectorizeText`** (vectorizes images & text).
- **Image Tagging**
    - Uses AI to identify image content (objects, actions, beings, scenery).
    - Image Analysis 4.0: Generates tags for thousands of entities in photos.
    - Evaluates entire image, not just main subjects.
    - Tags include: setting, activities, landscapes, colors, plants, etc.
- **Object Detection**
    - Like tagging but with bounding box coordinates for each object.
    - Example: Image with dog, cat, person – lists objects + pixel coordinates.
    - Useful for: Analyzing object relationships, finding multiple instances.
    - Limitation: Only finds objects/living things with bounding boxes.
    - Tagging provides context, e.g., "indoor".
- **Reading Text from Images (OCR)**
    - Extracts printed/handwritten text from images.
    - Unified performance-enhanced synchronous API.
        - Simplifies retrieval of OCR results.
        - Single API call, global language support.
    - Used for: OCR on non-text-heavy single images, near real-time UX.
- **Creating Thumbnails (Smart Cropping)**
    - Image Analysis 4.0: Uses Smart cropping.
        - Focus: Integral regions, people (bounding boxes) prioritized.
    - Smart cropping API:
        - Takes aspect ratios, returns bounding box coordinates.
        - App-configurable, crops/returns image based on coordinates.
- **People Detection**
    - Focus: Detecting people in images.
    - Returns: Bounding box coordinates, confidence score.
    - Doesn't classify or predict facial attributes.
- **Background Removal**
    - Feature in Image Analysis 4.0.
    - Splits image into segments: identifies objects or image parts.
    - Creates an alpha matte: separates foreground from background.
    - Utility: Isolate essential elements, analyze key features, ignore background noise.

## Vision Studio

Newest Azure Comp Vision tool:

- Provides unified portal experience for exploring, building and integrating functionality from Image Analysis 4.0 using a set of UI-based components
- Has a host of demo experiences ⇒

**Optical character recognition**:

- *Extract text from images*: Extract printed and handwritten text from images and documents

**Spatial analysis**:

- *Video summary and frame locator*: Generate a summary of the main points shown in a video, locate specific keywords, and jump to the relevant section of the video
- Count people in an area: Analyze real-time video to count the number of people in a designated zone
- Detect when people cross a line: Analyze real-time streaming video to detect when a person crosses a line
- Detect when people enter/exit a zone: Analyze real-time streaming video to detect when a person enters or exits an area
- Monitor social distancing: Analyze real-time streaming video to determine if people violate a distance rule

**Image analysis**:

- Search photos with natural language: Retrieve specific moments within a photo album based on vectorized text and image queries
- Add captions to images: Generate human-readable English sentences that describe the content of an image
- Dense captioning: Generate human-readable English phrases for all important objects within an image
- Detect common objects in images: Recognize objects of interested in an image and record their location using bounding boxes
- Extract common tags from images: Automatically assign one or more labels to an image based on its content
- Detect sensitive content in images: Moderate usage of images by detecting sensitive content

## Train custom models w Image Analysis 4.0

- Florence foundation: Boosts few-shot learning in Image Analysis 4.0.
- Use-cases: Image classification and object detection.
- **Image Classification**
    - Classify images based on primary subject (e.g., dog, landmark).
    - Train with pre-evaluated and labeled images.
- **Object Detection**
    - Identifies entities within an image.
    - Output: Object name, confidence score, and bounding box.
- **Model Training Components**
    - **Training Images**:
        - Collection of labeled images.
        - Stored in Azure Storage Account container.
        - Should have visual variety (angles, lighting, background).
        - More training images = better performance, though Florence offers good few-shot capabilities.
    - **COCO Files**:
        - File format to store info about training images and annotations.
        - Generated using Azure Machine Learning's data-labeling workflow.
        - JSON format: Indexes training images, labels, bounding boxes.
        - Essential fields: images, annotations, categories.
    - **Dataset Object**:
        - References the association file.
        - Needs to be created before training a model.
    - **Model Object**:
        - Represents a custom model in Image Analysis service.
        - Links with a Dataset for initial training.
        - Once trained, query the model using the Analyze Image API.

## Knowledge check

1. **Which Image Analysis 4.0 feature generates an English sentence describing image contents, plus descriptions for other objects and regions within the image?**
    1. Caption
    2. Dense Captions
    3. Tags
2. **Object detection models are used to do what?**
    1. Classify images based on their primary subject matter.
    2. Identify and categorize individual entities and their location within an image.
    3. Create a list of labels for an image.
3. **When using Vision Studio, what is the easiest way to generate a COCO annotation for a custom object detection model in Image Analysis 4.0?**
    1. Use the Azure Machine Learning data-labeling workflow.
    2. Use the Vision Studio COCO file generator utility after manually labeling images in the Dataset.
    3. Import a COCO file created manually in Visual Studio Code.