# Verizy
Verizy is an API-based identity document extraction and verification service.

## Features

### Extraction
Verizy mainly offers an extraction services wherein our proprietary algorithms are trained specifically to extract the right information reliably from our [supported documents](https://github.com/verizy/verizy-api/blob/master/v2/v2-supported-documents.md).

### Verification
Verizy offers a verification service on top of extracting information from documents. This is done employing various methods as listed below.
- Cross-verifying user-provide information with their document.
- Cross-Verifying multiple documents that belog to a user with one another and identifying differences.
- Verifying the extrtacted information from the document with verified government databases to ensure it's not a fraudulent one.

## API
The latest version of Verizy's API is at 2.0. The current version introduced asynchronous, queued, and web-hooked-based processing of requests.
- Documentation for Version 2.0 of Verizy can be found [here](https://github.com/verizy/verizy-api/blob/master/v2/v2-documentation.md).
- Documentation for Version 1.0 of Verizy can be found [here](https://github.com/verizy/verizy-api/blob/master/v1/v1-documentation.md).
