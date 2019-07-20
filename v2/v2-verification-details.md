# V2 Verification Details
The `VERIFICATION_DETAILS` object is a versatile object that depends on the business logic Verizy has implemented for specific use cases and clients. Essentially, this obect carries all data required to perform verification, that the client may need to pass us. The `verificationConfig` value that would be given to each client would determine how exactly the verification is performed by Verizy, and the structure of `verificationDetails`.
- In case of performing verification against user-provided data, the client needs to pass the user-provided data inside this object.
- In case of performing verification against the government records, this object can be `null` or empty as the details for verification would be fetched by Verizy from respective government sources.
- In case of performing a face match between a picture opf the user and their picture on the docuemnt, this image has to be passed inside the `verificationDetails` object.

## Possible Structures of `VERIFICATION_DETAILS`

```
{
    "userInfo": {
        ... //The parameters sent here would depend on the verification business logic Verizy has tailored for each client. This would be communicated separately at the time of integration.
    }
}
```

```
{
    "faceImageUrl": "<URL_OF_THE_IMAGE_SHOWING_THE_USER's_FACE>"
}
```
