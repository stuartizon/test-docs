---
title: Errors
---

# Errors
We use conventional HTTP response codes to indicate the success or failure of an API request.
In general, codes in the `2xx` range indicate success, codes in the `4xx` range indicate an error that failed given the information provided (e.g., a required parameter was omitted), and codes in the `5xx` range indicate a server error.
The service uses the following status codes:

`200 - OK`                    | Everything worked as expected.
`400 - Bad Request`           | The request was unacceptable, often due to missing a required parameter.
`408 - Timeout    `           | The request took too long to process - please try again later.
`428 - Precondition Required` | The region could not be inferred from the postcode - please resend with region parameter.
`5xx - Server Error`          | Something went wrong on our server.

### Response
The JSON response has the following structure:

code      | [ErrorCode](#errorCode) | a short string describing the overall error which occurred
errorList | [Error](#error)[]       | a list of errors

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

### <a name="errorCode">ErrorCode</a>

`Missing_Parameters`                | A required parameter was missing from the request
`Malformed_Parameters`              | A parameter value was incorrectly formatted (e.g. an illegal enumeration value)
`Malformed_Content`                 | The request body was malformed
`Validation_Error`                  | A parameter value failed a validation check (e.g. an illegal string in the postcode field)
`Qs_Quote_Community_Postcode_Error` | Postcode is not valid for this retailer
`Qs_Quote_Flow_Error`               | 3rd party quote generation error
`Qs_Quote_FutureSupply_Error`       | 3rd party quote generation error
`Qs_Quote_Region_Needed`            | Region required for this postcode
`Qs_Retrieve_Quote_Cache_Exception` | Cache error retrieving a quote, most likely due to expiration
`Qs_Save_Quote_Cache_Error`         | Cache error saving a quote
`Qs_TIL_Fuel_Error`                 | TIL does not contain the requested fuel type
`Qs_Unexpected_Region`              | Inferred region is not one we supply

### <a name="error">Error</a>

id          | `string` | a field or parameter containing an error
description | `string` | a short description of the error