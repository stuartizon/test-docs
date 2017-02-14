---
title: Quick Quote
---

# Quick Quote
Estimated quote based on the user's postcode, payment method and fuel type

### HTTP Request
`GET http://quote.prd.ptl.ovotech.org.uk/quick-quote`

### URL Parameters

Parameter       | Description                               | Type
--------------- | ----------------------------------------- | ----
retailer*       | OVO or community                          | [Retailer](#enums)
postcode*       | Postcode                                  | `string`
paymentMethod*  | Pay monthly or pay as you go              | [PaymentMethod](#enums)
fuel*           | Dual fuel or electricity only             | [Fuel](#enums)
serviceType*    | Online discount or full service           | [ServiceType](#enums)
region          | Electricity region [(see below)](#region) | [Region](#enums)

{% include enums.md %}

{% include region.md %}

### Response
The successful response is common to all the quote endpoints, and is detailed [here](quote-response).