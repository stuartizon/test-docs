---
layout: docs
title: Quick Quote
---

# Quick Quote
Estimated quote based on the user's postcode, payment method and fuel type

## HTTP Request
`GET http://quote.prd.ptl.ovotech.org.uk/quick-quote`

## URL Parameters

Parameter | Description | Type
--------- | ----------- | ----
retailer | OVO or community | `[OVO, Fairerpower, PeterboroughEnergy, SouthendEnergy, EnergySW]`
postcode | Postcode | string
paymentMethod | Pay Monthly _(default)_ or Pay As You Go | `[Paym, Payg]`
fuel | Dual Fuel _(default)_ or Electricity Only | `[Dual, Electricity]`
region | Electricity region for the quote - not usually required, but needs to be supplied if EHL cannot determine the energetic region from the postcode | `[EastEngland, EastMidlands, London, MerseysideAndNorthWales, NorthEastEngland, NorthernIreland, NorthWestEngland, NorthScotland, SouthEastEngland, SouthernEngland, SouthScotland, SouthWales, SouthWestEngland, WestMidlands, Yorkshire]`