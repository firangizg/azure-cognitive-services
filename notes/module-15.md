# 15. Analyze Images

Use the Analyze Image REST method or the equivalent method in SDK, specifying visual features you want to include. 

You can also use scoped funcs to retrieve specific subsets of the image features like description, tags and objects in the image. 

```json
{
  "categories": [
   {
     "name": "_outdoor_mountain",
     "confidence": "0.9"}
  ],
  "adult": {"isAdultContent": "false", …},
  "tags": [
    {"name": "outdoor", "confidence": 0.9},
    {"name": "mountain", " confidence ": 0.9}],
  "description": {
    "tags":["outdoor", "mountain"],
    "captions": [
      {"name": "A mountain with snow",
       "confidence": 0.9
      }
    ]
  },
  "metadata":
    {"width":60,"height":30, format:"Jpeg"},
  "faces": [],
  "brands": [],
  "color": {"dominantColorForeground": "Brown",…},
  "imageType": {"clipArtType": 0, …},
  "objects" : [
    {
     "rectangle": {x:20, y:25, w:10, h:20},
     "object": "mountain",
     "confidence": 0.9
    }
  ]
}
```

## Generate smart-cropped thumbnail

The Computer Vision service enables you to create a thumbnail with different dimensions (and aspect ratio) from  src image, and optionally to use image analysis to determine the *region of interest* in the image and make that the focus of the thumbnail. 

## Knowledge check

1. You want to use the Computer Vision Analyze Image function to generate an appropriate caption for an image. Which visual feature should you specify?
    1. Tags
    2. Description
    3. Categories
2. What is the purpose of the Computer Vision service?
    1. To provide functionality for audio transcription
    2. To extract info from images
    3. To detect the presence and location of specific sounds within an audio file