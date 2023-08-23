# 16. Analyze video

## Video Analyzer for Media

Designed to help you extract info from videos. Functionalities:

- Facial recognition: Requires Limited Access approval
- Optical character recognition - reading text in the video
- Speech transcription
- Topics
- Sentiment
- Labels
- Content moderation
- Scene segmentation

## Extract custom insights

Video Analyzer has predefined models recognizing celebrities, brands and trasncribing spoken phrases into text. You can extend the recognition capabilities by creating custom models for:

- People: images of faces u want recognized
- Language: specific terminologies
- Brands
- Animated characters

## Two ways of incorporating Video Analyzer for custom apps

1) Widgets: play, analyze and edit videos embedded into HTML iteface. 

2) Media API: REST API you can subscribe to get a key. Use the key to consume API and automate video indexing tasks like uploading and indexing videos, retrieving insights and determining endpoints for Video Analyzer widgets. 

## Knowledge check

1. **You want Video Analyzer for Media to analyze a video. What must you do first?**
    1. Use the Computer Vision service to extract key frames from the video
    2. Upload the video to Video Analyzer for Media and index it
    3. Store the video file in an Azure blob store container
2. **You want Video Analyzer for Media to recognize brands in videos recorded from conference calls. What should you do?**
    1. Edit the Brands model to show brands suggested by Bing, and add any new brands you want to detect
    2. Edit the conference call videos to include a caption of each brand seen on their first appearance
    3. Embed the Video Analyzer for Media widgets in a custom web site that has all the brand images stored for reference