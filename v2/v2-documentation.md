# Verizy V2 API Documentation
Documentation on [Verizy’s](https://verizy.ai) V2 document extraction and verification API services.

## What's new in V2?
- All `/extract` and `/verify` requests are queued by Verizy and are handled asynchronously.
- Results of all requests are pushed out using webhooks registered with us.
- Webhooks that are authenticated using a token provided by the client are supported.
- Only secure Webhooks that use a TLS connections over https are supported.

## Base URL
Verizy API service resides on the following URL.
`https://api2.verizy.ai/v2`

## Extraction Service
All of Verizy's document data extraction services reside on the endpoint mentioned below. Data extraction is performed using our proprietary character recognition engine, developed and trained specifically for the documents we support. The data given out is structured, and depends on the document that is being extracted.

### Request
#### URL
`/extract`
#### Method
`POST`
#### Headers
```javascript
"Content-Type": "application/json",
"api-key": "<API_KEY_PROVIDED_BY_VERIZY>"
```
#### Body
*application/json*
```javascript
{
	"document": {
		... //DOCUMENT object
	}
}
```
### Response
*application/json*
#### Success State
```javascript
{
    "code": 2001,
    "success": true,
    "result": {
        "requestId": "<REQUEST_ID_GENERATED_BY_VERIZY>"
    }
}
```
#### Failure States
**Discussion**: Treat `details` as optional as it would be sent only of the request had a body, it would be skipped otherwise. The `message` parameter gives a description of what went wrong.
```
{
    "code": 1007,
    "success": false,
    "message": "Invalid or missing document type.",
    "details": {
        ... //Information about the data sent in body during the request.
    }
}
```
```
{
    "code": 1002,
    "success": false,
    "message": "Missing or empty keys!. Client needs to send all mandatory keys"
}
```

**Discussion**: The response of `/extract` is just an acknowledgement that the request has been scheduled for immediate processing. The `requestId` will be the unique identifier for that request on Verizy. The `success` key tells if the request was accepted successfully or not. The `code` key is used for debuggin. The result of the requested process would be pushed to the client using webhooks. The eventual webhook content would also contain the same `requestId` in order to track the requests. 
### Webhook Response
#### Method
`POST`
#### Headers
```javascript
"Content-Type": "application/json",
```
**Discussion**: There will be another header key carrying the token/API-key, as determined by the client as a form of authentication.
#### Body
*application/json*
```javascript
{
	"requestId": "<REQUEST_ID_GENERATED_BY_VERIZY>",
	"completedTaskInfo": {
		"success": true, //Task completion status
		"extractedData": { //EXTRACTED_DATA object
			...
		}
	}
}
```


## Verification Service
All of Verizy's document verification services reside on the following endpoint. Document verification needs two inputs, the document(s) and the verification details. Verizy will analyze, extract, and process the document and verify the same.

### Request
#### URL
`/verify`
#### Method
`POST`
#### Headers
```
"Content-Type": "application/json",
"api-key": "<API_KEY_PROVIDED_BY_VERIZY>"
```
#### Body
*application/json*
```javascript
{
    "document": {
        ... //DOCUMENT object
    },
    "verificationDetails": {
	... //VERIFICATION_DETAILS object
    },
    "verificationConfig": "<VERIFICATION_CONFIG_ENUM_AS_GIVEN_BY_VERIZY>"
}
```
### Response
*application/json*
#### Success State
```javascript
{
    "code": 2001,
    "success": true,
    "result": {
        "requestId": "<REQUEST_ID_GENERATED_BY_VERIZY>"
    }
}
```
#### Failure States
**Discussion**: Treat `details` as optional as it would be sent only of the request had a body, it would be skipped otherwise. The `message` parameter gives a description of what went wrong.
```
{
    "code": 1007,
    "success": false,
    "message": "Invalid or missing document type.",
    "details": {
        ... //Information about the data sent in body during the request.
    }
}
```
```
{
    "code": 1002,
    "success": false,
    "message": "Missing or empty keys!. Client needs to send all mandatory keys"
}
```

**Discussion**: The response of `/verizy` is just an acknowledgement that the request has been scheduled for immediate processing. The `requestId` will be the unique identifier for that request on Verizy. The `success` key tells if the request was accepted successfully or not. The `code` key is used for debuggin. The result of the requested process would be pushed to the client using webhooks. The eventual webhook content would also contain the same `requestId` in order to track the requests.

## Miscellaneous
- `EXTRACTED_DATA` object is explained in detail [here](https://github.com/verizy/verizy-api/blob/master/v2/v2-extracted-data.md).
- `DOCUMENT` object is explained in detail [here](https://github.com/verizy/verizy-api/blob/master/v2/v2-document.md).
- `DOCUMENT_TYPE` object is explained in detail [here](https://github.com/verizy/verizy-api/blob/master/v2/v2-supported-documents.md).
- `VERIFICATION_DETAILS` object is explained in detail [here](https://github.com/verizy/verizy-api/blob/master/v2/v2-verification-details.md).
