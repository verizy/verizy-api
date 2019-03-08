# verizy-api
Documentation on Verizy’s document extraction and verification API.

## Extraction
----
All of Verizy's document data extraction services reside on two endpoints mentioned below. One allows you to send a file URL and get the extracted information and the other lets you upload the document directly to us and get extracted information. The responses of both endpoints will be similar, it’s the mechanism of sending us the document that differs.

### URL
/extraction

### Method
`POST`

### Headers
```
{
  “Content-Type”: ”application/json”,
	“api-key”: API_KEY_PROVIDED_BY_VERIZY
}
```

### Body
```
{
  “filePath”: URL_TO_THE_DOCUMENT,
	“docType”: DOCTYPE_VALUE
}
```
