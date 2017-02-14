---
title: Quote Response
---

# Quote Response
The quote object has the following structure:

quoteType     | Type of quote                         | [QuoteType](#enums)
postcode      | Postcode this quote is for            | `string`
fuel          | Fuel type this quote is for           | [Fuel](#enums)
paymentMethod | Payment method this quote is for      | [PaymentMethod](#enums)
serviceType   | Is quote for the online discount?     | [ServiceType](#enums)
economy7      | Is quote for economy 7 tariffs?       | `boolean`
dateCreated   | Date on which the quote was generated | `date`[^1]
region        | Electricity region                    | [Region](#enums)
currentSupply | Details about the current tariffs     | Map[[Utility](#enums), [CurrentSupply](#currentSupply)]
tariffs       | Details about the OVO tariffs         | Map[[TariffId](#enums), [Tariff](#tariff)]

The currentSupply contains entries for each utility type.
If the quote is for dual fuel, there will be entries for `Gas` and `Electricity`.
If the quote is for electricity only, there will only be an entry for `Electricity`.

```json
{
    "quoteType": "Quick",
    "postcode": "SW0 1AE",
    "fuel": "Electricity",
    "paymentMethod": "Paym",
    "serviceType": "Online",
    "economy7": false,
    "dateCreated": "2016-05-13",
    "region": "SouthernEngland",
    "currentSupply": ...,
    "tariffs": ...
}
```

### <a name="currentSupply">CurrentSupply</a>

supplier      | Name of the current supplier | `string`
tariff        | Name of the current tariff   | `string`
annualUsage   | KWh used per year            | `integer`
annualSpend   | Cost per year (in GBP)       | `float`

```json
{
    "supplier": "British Gas",
    "tariff": "Standard",
    "annualUsage": 12500,
    "annualSpend": 583.181
}
```

### <a name="tariff">Tariff</a>

name                    | Display name of this tariff                 | `string`
description (optional)  | Brief description of the tariff             | `string`
tagline (optional)      | Tagline information                         | `string`
renewableFuelPercentage | Percentage renewable electricity            | `integer`
exitFees                | Fees charged for early exit                 | `integer`
discount                | Tariff total discounts                      | `integer`
contractLength          | Contract length in months                   | `integer`
variable                | Is this a variable tariff?                  | `boolean`
expectedAnnualSpend     | Expected cost per year (in GBP)             | `float`
expectedAnnualSavings   | Expected savings compared to current supply | `float`
tils                    | Tariff Information Label details            | Map[[Utility](#enums), [TIL](#til)]

```json
{
    "displayName": "Better Energy",
    "tagline": "Start saving",
    "description": "Big savings and get fixed rates for a year",
    "renewableFuelPercentage": 33,
    "exitFees": 0,
    "discount": 60,
    "contractLength": 12,
    "variable": false,
    "expectedAnnualSavings": 123,
    "expectedAnnualSpend": 1049,
    "tils": ...
}
```

### <a name="til">TIL</a>

name                    | Industry standard name for this tariff      | `string`
supplierName            | Industry standard name for the supplier     | `string`
paymentMethod           | Industry standard payment method name       | `string`
unitCharge              | Cost (in p) per KWh                         | `float`
standingCharge          | Daily standing charge (in p)                | `float`
tariffEndDate           | End date of this tariff                     | `date`[^1]
exitFees                | Fees charged for early exit (this utility)  | `float`
discount                | Tariff discounts (this utility)             | `float`
annualUsage             | Expected KWh used per year                  | `integer`
annualSpend             | Expected cost per year (in GBP)             | `float`
comparisonRate          | Expected daily cost based on annualUsage    | `float`

```json
{
    "name": "OVO Energy - Better Energy Fixed (All Online)",
    "supplierName": "OVO Energy",
    "paymentMethod": "Monthly Direct Debit",
    "unitCharge": 11.03,
    "standingCharge": 28.77,
    "tariffEndDate": "2017-05-13",
    "exitFees": 0,
    "discount": 30,
    "annualUsage": 3100,
    "annualSpend": 446.94,
    "comparisonRate": 13.45
}
```

{% include enums.md %}

### Example Response
```json
{
    "quoteType": "Quick",
    "postcode": "SW0 1AE",
    "fuel": "Electricity",
    "paymentMethod": "Paym",
    "serviceType": "Online",
    "economy7": false,
    "dateCreated": "2016-05-13",
    "region": "SouthernEngland",
    "currentSupply": {
      "Electricity": {
        "supplier": "British Gas",
        "tariff": "Standard",
        "annualKWh": 12500,
        "annualSpend": 583.181,
        "estimatedMonthlyCost": 48.6
      }
    },
    "tariffs": {
      "Fixed": {
        "displayName": "Better Energy",
        "tagline": "Start saving",
        "description": "Big savings and get fixed rates for a year",
        "renewableFuelPercentage": 33,
        "exitFees": 0,
        "discount": 60,
        "contractLength": 12,
        "variable": false,
        "expectedAnnualSavings": 123,
        "expectedAnnualSpend": 1049,
        "tils": {
          "Electricity": {
            "name": "OVO Energy - Better Energy Fixed (All Online)",
            "supplierName": "OVO Energy",
            "paymentMethod": "Monthly Direct Debit",
            "unitCharge": 11.03,
            "standingCharge": 28.77,
            "tariffEndDate": "2017-05-13",
            "exitFees": 0,
            "discount": 30,
            "annualUsage": 3100,
            "annualSpend": 446.94,
            "comparisonRate": 13.45
          },
          "Gas": {
            "name": "OVO Energy - Better Energy Fixed (All Online)",
            "supplierName": "OVO Energy",
            "paymentMethod": "Monthly Direct Debit",
            "unitCharge": 2.6,
            "standingCharge": 28.77,
            "tariffEndDate": "2017-05-13",
            "exitFees": 0,
            "discount": 30,
            "annualUsage": 12500,
            "annualSpend": 430.01,
            "comparisonRate": 3.2
          }
        }
      }
    }
  }
}
```

[^1]: Dates are in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format