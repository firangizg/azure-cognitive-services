# 13. Translate text w the Translator service

Translator service provides a multilingual text transition API that you can use for:

- Language detection
- One-to-many translation
- Script transliteration (convert text from its native script to an alternative script)

## Understand lang detection, translation and transliteration

### Language detection

**detect** REST function: to detect the language in which text is written

If you submit this request:

```json
{ 'Text' : 'こんにちは' }
```

Response:

```json
[
  {
    "isTranslationSupported": true,
    "isTransliterationSupported": true,
    "language": "ja",
    "score": 1.0
   }
]
```

### Translation

Translate text from one lang to another, use the translate function; specify a single from parameter to indicate the src lang, and one or more parameters to specify the lang into which you want the text translated.

Ex: with the request above, if you specified a from parameter of (ja) and 2 to parameters w the values (en) and (fr), it would produce:

```json
[
  {"translations": 
    [
      {"text": "Hello", "to": "en"},   
      {"text": "Bonjour", "to": "fr"}
    ]
  }
]
```

## Specify translation options

Translate func supports numerous parameters that affect the output. 

- You can use includeAlignment parameter with a value of true.
- includeSentenceLength
- profanityAction parameter
    - NoAction
    - Deleted
    - Marked (profanityMarker)

## Define custom translations

Default translation model is effective for general translation, but u can create a custom model that maps ur own sets of src and target terms for translation for more customized mdoel. Use the Custom Translator portal to:

1. Create a workspace linked to your Translator resource
2. Create a project
3. Upload training data files
4. Train a model

Ur custom model has a unique category id, which u can specify in translate calls to your Translator resource by using the category parameter, causing translation to be performed by ur custom mdoel instead of the default model. 

## Knowledge check

1. What function of the Translator service should you use to convert the Chinese word "你好" to the English word "Hello"?
    1. detect
    2. translate
    3. transliterate
2. What function of the Translator service should you use to convert the Russian word "спасибо" in Cyrillic characters to "spasibo" in Latin characters?
    1. detect
    2. translate
    3. transliterate