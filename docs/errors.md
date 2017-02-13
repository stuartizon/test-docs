---
title: Errors
---

# Errors
We use conventional HTTP response codes to indicate the success or failure of an API request.
In general, codes in the `2xx` range indicate success, codes in the `4xx` range indicate an error that failed given the information provided (e.g., a required parameter was omitted), and codes in the `5xx` range indicate a server error.
The service uses the following status codes:

`200 - OK`           | Everything worked as expected.
`400 - Bad Request`  | The request was unacceptable, often due to missing a required parameter.
`5xx - Server Error` | Something went wrong on our server.

### Response
The JSON response has the following structure:

code      | `ErrorCode` | a short string describing the overall error which occurred
errorList | `Error[]`   | a list of errors

An example response:

```json
{
    "code": "Validation_Error",
    "errorList": [{
        "id": "postcode",
        "description": "Illegal characters in postcode"
    }]
}
```

### ErrorCode

Missing_Parameters   | A required parameter was missing from the request
Malformed_Parameters | A parameter value was incorrectly formatted (e.g. an illegal enumeration value)
Malformed_Content    | The request body was malformed
Validation_Error     | A parameter value failed a validation check (e.g. an illegal string in the postcode field)

### Error

id          | `string` | a field or parameter containing an error
description | `string` | a short description of the error