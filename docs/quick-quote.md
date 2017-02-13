---
title: Quick Quote
---

# Quick Quote
Estimated quote based on the user's postcode, payment method and fuel type

## HTTP Request
`GET http://quote.prd.ptl.ovotech.org.uk/quick-quote`

## URL Parameters

Parameter      | Description                     | Type
-------------- | ------------------------------- | ----
retailer*      | OVO or community                | `[OVO, Fairerpower, PeterboroughEnergy, SouthendEnergy, EnergySW]`
postcode*      | Postcode                        | string
paymentMethod* | Pay monthly or pay as you go    | `[Paym, Payg]`
fuel*          | Dual fuel or electricity only   | `[Dual, Electricity]`
serviceType*   | Online discount or full service | `[Online, FullService]`
region         | Electricity region (see below)  | `[EastEngland, EastMidlands, London, MerseysideAndNorthWales, NorthEastEngland, NorthernIreland, NorthWestEngland, NorthScotland, SouthEastEngland, SouthernEngland, SouthScotland, SouthWales, SouthWestEngland, WestMidlands, Yorkshire]`

## Region
The region is not usually required to generate a quote, as EHL can in general infer the energetic region from the provided postcode.
However there are a small number of postcodes for which EHL cannot infer the region - e.g. new builds.
If EHL cannot determine the region for a given postcode and the region parameter has not been provided, the response to this endpoint will be `428 - Precondition Required`.

In this circumstance the request needs to be resent with the region parameter provided.