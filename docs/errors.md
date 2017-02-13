---
title: Errors
---

# Errors
We use conventional HTTP response codes to indicate the success or failure of an API request.
In general, codes in the `2xx` range indicate success, codes in the `4xx` range indicate an error that failed given the information provided (e.g., a required parameter was omitted), and codes in the `5xx` range indicate a server error.
The quote service uses the following error codes:

Error Code | Meaning
---------- | -------
400        | Bad Request - your request is malformed
500	       | Internal Server Error – we had an unexpected problem with our server