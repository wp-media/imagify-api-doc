# Errors

Imagify API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request was not understandable
422 | Already compressed -- Your image is already compressed
403 | Forbidden -- You don't have the proper right to access the data
404 | Not Found -- The specified ressource could not be found
405 | Method Not Allowed -- You tried to access an endpoint with an invalid method
415 | Unsupported media type -- The file you've uploaded is not supported
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarially offline for maintanance. Please try again later.
