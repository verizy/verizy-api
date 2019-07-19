# V2 Document

The `DOCUMENT` object represents a single document, carries URLs for images of the document. These are the possible ways a `DOCUMENT` object could be constructed.

a. One URL per document
```javascript
{
    "mainUrl": "<URL_OF_IMAGE>",
    "documentType": "<DOCUMENT_TYPE_ENUM>"
}
```

b. Two URLs per document, one for front side and another for the back side of the document
```javascript
{
    "frontUrl": "<URL_OF_IMAGE>",
    "backUrl": "<URL_OF_IMAGE>",
    "documentType": "<DOCUMENT_TYPE ENUM>"
}
```
