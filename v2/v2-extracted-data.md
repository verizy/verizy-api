# V2 Extracted Data

The `EXTRACTED_DATA` Object can be of various formats, depending on the `documentType` the extracted data represents. The keys that represent similar data across all documents use the same key names. All the keys that represent unique data have their own key names. Treat all parameters as optional (could be `null` or not exist), as it depends on the success of extracton and the quality of the document.

## Aadhaar
`documentType: aadhaar`

```
{
    "documentType": "aadhaar",
    "aadhaarId": "<AADHAAR_NUMBER>",
    "dob": "<DATE_OF_BIRTH>", //Formats - (dd/MM/yyyy) or (yyyy)
    'name': "<NAME_OF_THE_DOCUMENT_HOLDER>",
    'fatherName': "<NAME_OF_THE_DOCUMENT_HOLDER'S_FATHER>",
    'gender': "<GENDER_OF_THE_DOCUMENT_HOLDER>",
    'address': "<ADDRESS_OF_THE_DOCUMENT_HOLDER>"
}  
```
*Treat all parameters as optional.*

## PAN Card
`documentType: pan`

```
{
    "documentType": "pan",
    "panId": "<PAN_ID>",
    "dob": "<DATE_OF_BIRTH>", //Formats - (dd/MM/yyyy)
    "name": "<NAME_OF_THE_DOCUMENT_HOLDER>",
    "fatherName": "<NAME_OF_THE_DOCUMENT_HOLDER'S_FATHER>",
}  
```
*Treat all parameters as optional.*

## Driver's License
`documentType: dl`

```
{
    "documentType": "dl",
    "dlId": "<DL_ID>",
    "dob": "<DATE_OF_BIRTH>", //Formats - (dd/MM/yyyy)
    "name": "<NAME_OF_THE_DOCUMENT_HOLDER>",
    "doi": "<DATE_OF_ISSUE>", //Formats - (dd/MM/yyyy)
    "doe": "<DATE_OF_EXPIRATION>", //Formats - (dd/MM/yyyy)
    "state": "<STATE_IN_INDIA_THE_DL_BELONGS_TO>"
}  
```
*Treat all parameters as optional.*

## Voter's ID Card
`documentType: voter_id`

```
{
    "documentType": "voter_id",
    "voterId": "<VOTER_ID>",
    "name": "<NAME_OF_THE_DOCUMENT_HOLDER>",
    "guardianName": "<NAME_OF_THE_DOCUMENT_HOLDER'S_GUARDIAN>",
}  
```
*Treat all parameters as optional.*

## Udyog Aadhaar
`documentType: udyog_aadhaar`

```
{
    "documentType": "udyog_aadhaar",
    "udyogAadhaarId": "<UDYOG_AADHAAR_NUMBER>",
    "aadhaarId": "<AADHAAR_NUMBER>",
    "panId": "<PAN_ID>",
    "entrepreneurName": "<NAME_OF_THE_ENTREPRENEUR>",
    "gender": "<GENDER_OF_THE_DOCUMENT_HOLDER>",
    "enterpriseName": "<NAME_OF_THE_ENTERPRISE>"
}  
```
*Treat all parameters as optional.*
