# Verizy API Documentation
Documentation on Verizy’s document extraction and verification API services.

## Extraction Service
All of Verizy's document data extraction services reside on two endpoints mentioned below. One allows you to send a file URL and get the extracted information and the other lets you upload the document directly to us and get extracted information. The responses of both endpoints will be similar, it’s the mechanism of sending us the document that differs.

### 1. Extract
#### URL
/extract
#### Method
`POST`
#### Headers
```
“Content-Type”: ”application/json”,
“api-key”: API_KEY_PROVIDED_BY_VERIZY
```
#### Body
*application/json*
```javascript
{
  “filePath”: URL_TO_THE_DOCUMENT,
  “docType”: DOCTYPE_VALUE
}
```
### 2. Upload and Extract
#### URL
/upload-and-extract
#### Method
`POST`
#### Headers
```
“Content-Type”: ”multipart/form-data”,
“api-key”: API_KEY_PROVIDED_BY_VERIZY
```
#### Body
##### Scenario 1: Direct FIle Upload
*multipart/form-data*
```
“file”: FILE_DATA
“docType”: DOCKTYPE_VALUE
```
##### Scenario 2: Base64 Encoded File Upload
*multipart/form-data*
```
“base64File”: BASE_64_Encoded_FILE_DATA
“fileMIMEType”: MIME_TYPE_OF_THE_SENT_FILE
“docType”:DOCKTYPE_VALUE
```
> **Discussion**: If you send file, do not include base64File parameter and if you send base64File please include the fileMIMEType and do not include the file parameter.

### Making Sense of Extraction Response
