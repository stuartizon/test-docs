---
title: Quote Response
---

# Quote Response
Response containing the structured quote object

## Example Response
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