## Errors

Earthport uses conventional HTTP response codes to indicate the success or failure of an API request. In general: Codes in the 2xx range indicate success. Codes in the 4xx range indicate an error that failed given the information provided (e.g., a required parameter was omitted, a charge failed, etc.). Codes in the 5xx range indicate an error with Earthport's servers.

Some 4xx errors that could be handled programmatically (e.g., a bank account is invalid) include an error code that briefly explains the error reported.

### HTTP status codes

| Code        | Description           |
| ---------------|-------------------------- |
| **200**   | OK. Successful request. |
| **204**   | OK. Successful request but no response is returned. This is returned by some delete and update APIs. |
| **400**   | Bad request. Request message data did not pass validation. |
| **401**   | Unauthorised. Not authorised to access requested data. |
| **403**   | Forbidden. Access to requested data is forbidden. |
| **404**   | Not Found. Requested resource does not exist. |
| **408**   | Timeout. Operation timed out. |
| **415**   | Unsupported media type. This is probably due to submitting incorrect data format. e.g. XML instead of JSON. |
| **429**   | Too many requests hit the API too quickly. We recommend an exponential backoff of your requests. |
| **500**   | Earthport server error. |

### Validation errors

Earthport has defined a standard Error Response structure for both validation (4xx) and application errors (5xx).

This response will indicate whether the error is a validation type error and it will contain an array listing each validation error.


```javascript
{
  "timeOfFailure": "2018-07-19T10:22:15.529+00:00",
  "failureType": "validation",
  "shortMsg": "Beneficiary Bank Account failed validation process",
  "longMsg": "BeneficiaryBankAccount has failed validation",
  "code": 12000,
  "uniqueErrorID": "1TWZLQGL9ZQUQ",
  "failures": {
    "failure": [
      {
        "key": "bankAccountDetails.bankName",
        "code": 12041,
        "value": "Beneficiary Bank Name not supplied"
      },
      {
        "key": "bankAccountDetails.sortCode",
        "code": 12201,
        "value": "Beneficiary Bank Account Sort Code supplied is too long"
      }
    ]
  }
}
```