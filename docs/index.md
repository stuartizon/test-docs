---
layout: docs
---

# Quote Service
Microservice for generating energy quotes

## Types of quotes
This service provides endpoints for the following types of quotes:

* Quick quote - this is an estimate based on the user's postcode, payment method and fuel type
* Full quote - this provides an exact quote usage actual consumption values, or can provide a more detailed estimate based upon some property details

# Quick quote

Parameter | Description
--------- | -----------
postcode  | postcode