# Verizy V2 API Documentation
Documentation on [Verizy’s](https://verizy.ai) V2 document extraction and verification API services.

## Base URL
Verizy API service resides on the following URL.
`https://api2.verizy.ai/v2`

## Extraction Service
All of Verizy's document data extraction services reside on two endpoints mentioned below. One allows you to send a file URL and get the extracted information and the other lets you upload the document directly to us and get extracted information. The responses of both endpoints will be similar, it’s the mechanism of sending us the document that differs.

### 1. Extract
#### URL
`/extract`
#### Method
`POST`
#### Headers
```
"Content-Type": "application/json",
"api-key": API_KEY_PROVIDED_BY_VERIZY
```
#### Body
*application/json*
```javascript
"document": { //DOCUMENT object type
    ...
}
```
##### `DOCUMENT` Object
The `DOCUMENT` object represents a single document, carries URLs for images of the document. These are the possible ways a `DOCUMENT` object could be constructed.

a. One URL per document
```
{
    "mainUrl": URL_OF_IMAGE,
    "type": DOCUMENT_TYPE_ENUM
}
```

b. Two URLs per document, one for front side and another for the back side of the document
```
{
    "frontUrl": URL_OF_IMAGE,
    "backUrl": URL_OF_IMAGE,
    "type": DOCUMENT_TYPE_ENUM
}
```
##### `DOCUMENT_TYPE` Object
| DOCUMENT_TYPE ENUM | Description |
|--------------------|-------------|
| `aadhaar` | Aadhaar Card |
| `pan` | PAN Card |
| `dl` | Driver's License |
| `voter_id` | Voter's ID Card |
| `gst` | GST Registration Document (REG-06 & REG-25) |
| `form_16` | Form 16 |
| `itr` | Income Tax Return |
| `salary_slip` | Salary Slip |

### Things to Note
- If you send `file`, do not include `base64File` parameter and if you send `base64File` please include the `fileMIMEType` and do not include the `file` parameter. The supported `fileMIMEType` values are shown in [this table](https://github.com/verizy/verizy-api/blob/master/SupportedMIMETypes.md).
- `filePath`: Make sure the URL leads to the image or document resource directly without redirections.
- `docType`: Mentioning the document type is important to detect the relevant document and the extraction of data. The valid values of this key are mentioned in [this table](https://github.com/verizy/verizy-api/blob/master/SupportedDocuments.md).
- `api-key`: This is important to gain access to our services and to track the usage.

### Making Sense of Extraction Response
- The response will always be in *application/json* format.
- The response would contain a `success` key denoting if the extraction process succeeded or not.
- The response would have other parameters specific to the document extracted.

## Verification Service
All of Verizy's document verification services reside on the following endpoint. Document verification needs two inputs, the document as an image or a pdf and the user-entered details. Verizy will analyze, extract, and process the document and compare the extracted details with what’s entered by the user. The comparison result determines if the given information match, don’t match or if our algorithm is unsure. The unsure status is given only in situations where the algorithm isn’t able to extract and detect some of the details it needs to perform the verification.

### Verify
#### URL
`/verify`
#### Method
`POST`
#### Headers
```
"Content-Type": "application/json",
"api-key": API_KEY_PROVIDED_BY_VERIZY
```
#### Body
*application/json*
```javascript
{
  "filePath": URL_TO_THE_DOCUMENT,
  "docType": DOCTYPE_VALUE,
  "verificationConfig": PROVIDED_BY_VERIZY,
  "userInfo": {
    "firstName": FIRST_NAME,
    "middleName": MIDDLE_NAME,
    "lastName": LAST_NAME,
    "idNumber": ID_NUMBER,
    "dob": DATE_OF_BIRTH,
    "state": STATE
  }
}
```
### Things to Note
- The `userInfo` object in the request body will contain the user-entered information that the document needs to be verified against.
- The `filePath` should always allow us to directly access the document.
- The `dob` should always be sent in this format: *yyyy-MM-dd* e.g. *2000-01-24*.
- The `state` should be the full state name.
- The `verificationConfig` allows us to distinguish between the different verification business logics that we support. We will tailor one to your use case, if needed. Just contact us.
