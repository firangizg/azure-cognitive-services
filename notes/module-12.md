# 12. Extract insights from text w the Language service

## Provision a Language resource

The Language service designed to help extract info from text. You can use it for:

- Lang detection
- Key phrase extraction
- Sentiment analysis
- Named entity recognition
- Entity linking

## Detect language

Language Detection API evaluates text input, for each doc submitted, returns lang identifiers w a score indicating the strength of the analysis. 

- Useful for content stores that collect arbitraty text where lang is unknown

Doc size must be under 5,120 characters. Each collection is restriced to 1,000 items. 

A sample JSON payload u might submit to the service in the request body:

```json
{
  "documents": [
    {
      "countryHint": "US",
      "id": "1",
      "text": "Hello world"
    },
    {
      "id": "2",
      "text": "Bonjour tout le monde"
    }
  ]
}
```

The service will return a JSON response containing a result for each document in the request body, including predicted lang and a vlaue indicating the confidence level of the prediction. 

```json
{
  "documents": [
   {
     "id": "1",
     "detectedLanguage": {
       "name": "English",
       "iso6391Name": "en",
       "confidenceScore": 1
     },
     "warnings": []
   },
   {
     "id": "2",
     "detectedLanguage": {
       "name": "French",
       "iso6391Name": "fr",
       "confidenceScore": 1
     },
     "warnings": []
   }
  ],
  "errors": [],
  "modelVersion": "2020-04-01"
}
```

Mixed lang content within the same doc returns lang w the largest representation in the content, w a lower positive rating, reflecting the marginal strength of that assessment. In the following example, the analyzer uses statistical analysis of the text to determine the predominant language

```json
{
  "documents": [
    {
      "id": "1",
      "text": "Hello, I would like to take a class at your University. ¿Se ofrecen clases en español? Es mi primera lengua y más fácil para escribir. Que diriez-vous des cours en français?"
    }
  ]
}
```

The response:

```json
{
  "documents": [
    {
      "id": "1",
      "detectedLanguages": [
        {
          "name": "Spanish",
          "iso6391Name": "es",
          "score": 0.9375
        }
      ]
    }
  ],
  "errors": []
}
```

Last condition to consider is when there is ambiguity to the language content. If textual content is not something parseable ⇒ NaN. 

```json
{
      "id": "5",
      "detectedLanguages": [
        {
          "name": "(Unknown)",
          "iso6391Name": "(Unknown)",
          "score": "NaN"
        }
      ]
```

## Analyze sentiment

You could submit a single doc for sentiment analysis like:

```json
{
  "documents": [
    {
      "language": "en",
      "id": "1",
      "text": "Smile! Life is good!"
    }
  ]
}
```

Response from the service might look like:

```json
{
  "documents": [
   {
     "id": "1",
     "sentiment": "positive",
     "confidenceScores": {
       "positive": 0.99,
       "neutral": 0.01,
       "negative": 0.00
     },
     "sentences": [
       {
         "text": "Smile!",
         "sentiment": "positive",
         "confidenceScores": {   
             "positive": 0.97,
	         "neutral": 0.02, 
             "negative": 0.01
           },
         "offset": 0,
         "length": 6
       },
       {
	      "text": "Life is good!",
          "sentiment": "positive",
          "confidenceScores": {   
             "positive": 0.98,
	         "neutral": 0.02,  
             "negative": 0.00
           },
         "offset": 7,
         "length": 13
       }
     ],
     "warnings": []
   }
  ],
  "errors": [],
  "modelVersion": "2020-04-01"
}
```

Sentence sentiment is based on confidence scores for pos, neg and neutral. 

Overall is based on sentences:

- if all sentences neutral, overall sentiment = neutral
- only positive + neutral ⇒ positive
- neg + neutral ⇒ negative
- pos + neg ⇒ mixed

## Extract linked entities

Entity linking is used to disambiguate entities of the same name by referencing an article in knowledge base. Wikipedia provides knowledge base for the Text Analytics service. 

Submit one/more doc for analysis:

```json
{
  "documents": [
    {
      "language": "en",
      "id": "1",
      "text": "I saw Venus shining in the sky"
    }
  ]
}
```

Response includes entities identified and the links to associated articles:

```json
{
  "documents":
    [
      {
        "id":"1",
        "entities":[
          {
            "name":"Venus",
            "matches":[
              {
                "text":"Venus",
                "offset":6,
                "length":5,
                "confidenceScore":0.01
              }
            ],
            "language":"en",
            "id":"Venus",
            "url":"https://en.wikipedia.org/wiki/Venus",
            "dataSource":"Wikipedia"
          }
        ],
        "warnings":[]
      }
    ],
  "errors":[],
  "modelVersion":"2020-02-01"
}
```

## Knowledge Check

**1. How should you create an application that monitors the comments on your company's web site and flags any negative posts?**

- Use the Language service to extract key phrases.
- Use the Language service to perform sentiment analysis of the comments.
- Use the Language service to extract named entities from the comments.

**2. You have analyzed text that contains the word "Paris". How might you determine of this word refers to the French city or the character in Homer's "The Iliad"?**

- Use the Language service to extract key phrases.
- Use the Language service to detect the language of the text.
- Use the Language service to extract linked entities.