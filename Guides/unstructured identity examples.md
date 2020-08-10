Below is the **JSON** example for both Unstructured Identity **'Payer'** and **'Beneficiary'**

*For the list of field names that are **Mandatory** and **Optional** for Payer and Beneficiary, please refer to the [Unstructured Key Names](#/http/models/enumerations/unstructured-key-names) page*

### Payer

``` 
{
    "userID": {
        "merchantUserID": "userID_{{current_time_in_ms}}"
    },
    "accountCurrency": "any",
    "payerIdentity": {
        "unstructuredIdentity": [
            {
                "key": "Name",
                "value": "John Smith"
            },
            {
                "key": "AddressLine1",
                "value": "20 Aldersgate St"
            },
            {
                "key": "AddressLine2",
                "value": "Optional"
            },
            {
                "key": "AddressLine3",
                "value": "Optional"
            },
            {
                "key": "Country",
                "value": "GB"
            }
        ]
    }
}
```

### Beneficiary

```
{
    "benBankID": {
        "merchantBankID": "bankID_{{current_time_in_ms}}"
    },
    "beneficiaryIdentity": {
        "unstructuredIdentity": [
            {
                "key": "Name",
                "value": "John Smith"
            },
            {
                "key": "AddressLine1",
                "value": "20 Aldersgate St"
            },
            {
                "key": "AddressLine2",
                "value": "Optional"
            },
            {
                "key": "AddressLine3",
                "value": "Optional"
            },
            {
                "key": "Country",
                "value": "GB"
            }
        ]
    },
    "description": "J Smith current account",
    "countryCode": "GB",
    "currencyCode": "GBP",
    "bankAccountDetails": [
        {
            "key": "accountNumber",
            "value": "06970093"
        },
        {
            "key": "accountName",
            "value": "Mr. J Smith"
        },
        {
            "key": "bankName",
            "value": "Barclays Bank"
        },
        {
            "key": "sortCode",
            "value": "800554"
        }
    ]
}
```