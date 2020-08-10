Webhooks are used to be notified about events occurring on your account.

Visa Payments Limited can send webhook events that notify your application any time an event happens on your account. This is especially useful for events, for instance when a payment is rejected or returned, or when a deposit is made to your account.

Webhooks are sent asynchronously and are not guaranteed to be delivered in order. We recommend that applications protect against duplicated events by making event processing idempotent.

* You must use SSL/TLS for webhook URLs. Unsecured webhook URLs are only allowed in the sandbox environment.
* Webhooks include an 'Earthport-Origin' header indicating which Visa Payments Limited environment they were sent from. This will be `https://api.earthport.com` for production, and `https://api-sandbox.earthport.com` for sandbox.
* If you are validating webhook signatures then your endpoint should return a "498 Token Invalid" error - should the signature be invalid.
* You may optionally choose to whitelist Visa Payments Limited webhook IP addresses (52.210.35.14 or 34.242.162.91).

### Signing webhooks

Visa Payments Limited signs the body of the POST request with an HMAC SHA256 digest, using the client_id and secret key of the client.

This signature is then set in an HTTP Header "Earthport-Signature" along with the HTTP Header "Earthport-Client-Id".

We have a [sample Java project on Github](https://github.com/Earthport/Webhook-Signature-Decoder) which shows how the signing algorithm works and how you could decode and verify the signature.

### HTTP Headers

| HTTP Header   | Description                                             | Example |
| -------------------- |---------------------------------------------------| ------ |
| Earthport-Client-Id          | The client_id is used during authentication with the REST APIs. | y9OJrEnfV6ZHFospsQSeSiJqhfaUD6lH |
| Earthport-Signature      | Signature which can be used to verify the notification is valid and from Visa Payments Limited | 1544701184264.V38kC60MSXVqZtcNLMr0upPvv0gBPEKlIVfLB0wB1kI= |
| Earthport-Origin      | The Visa Payments Limited environment which generated the notification. This is useful when troubleshooting unexpected notifications. Notifications are either generated from Production or Sandbox. |  api-sandbox.earthport.com |

### Acknowledgement and retries

When your application receives a webhook, it should respond with an HTTP 200 status code to indicate successful receipt. If Visa Payments Limited receives a status code other than 200, or your application fails to provide a valid respond within 60 seconds of the attempt, another attempt will be made.

Visa Payments Limited will re-attempt delivery every 15 minutes over the course of 24 hours.

We need to respond with the following format:

```json
{
   "ackMessage":"DONE",
   "epTransactionID":281474990733677
}
``` 

### Webhook event types

#### Deposit event
A notification is sent when funding is applied to a user VAN.

```
{
  "notificationType": "DEPOSIT",
  "epUserID": 3430090154193,
  "merchantUserIdentity": "cptt001",
  "epTransactionID": 281474990733677,
  "timestamp": "2015-02-03T09:34:43.193+00:00",
  "managedMerchantIdentity": "Contracting Merchant User",
  "depositAmount": {
    "currency": "EUR",
    "amount": 12.5
  },
  "depositedAmount": {
    "currency": "GBP",
    "amount": 10.26
  }
}
```

#### Funding event
A notification is sent when funding is applied to the merchant's central VAN.

```
{
  "notificationType": "FUNDING",
  "epUserID": 3430090146574,
  "merchantUserIdentity": "Central_EarthportPaymentTest",
  "epTransactionID": 281474984542458,
  "timestamp": "2018-10-16T15:04:16.140+00:00",
  "depositAmount": {
    "currency": "GBP",
    "amount": 88888
  },
  "transactionDetails": "kklkj8888"
}
```


#### Rejected Payout event
A notification is sent when a payment is rejected by Visa Payments Limited or a banking partner.

```
{
  "notificationType": "REJECTED_PAYOUT",
  "epUserID": 3430090154301,
  "merchantUserIdentity": "119TUOC87NPCK",
  "epTransactionID": 281474990733689,
  "timestamp": "2015-02-03T18:22:07.211+00:00",
  "managedMerchantIdentity": "Contracting Merchant User",
  "refundedAmount": {
    "currency": "GBP",
    "amount": 100
  },
  "payoutAmount": {
    "currency": "GBP",
    "amount": 100
  },
  "payoutTransactionID": {
    "epTransactionID": 281474990732857,
    "merchantTransactionID": "IntegrationTest:11903175"
  },
  "epBankID": 9670429,
  "reason": " Account Address invalid . BE04",
  "reasonID": 101
}
```

#### Refund event
A notification is sent when a payment is returned from the beneficiary bank, which then initiates a refund.

```
{
  "notificationType": "REFUND",
  "epUserID": 3430090154193,
  "merchantUserIdentity": "cptt001",
  "epTransactionID": 281474990733696,
  "timestamp": "2015-02-03T18:35:13.485+00:00",
  "managedMerchantIdentity": "Contracting Merchant User",
  "refundedAmount": {
    "currency": "EUR",
    "amount": 58.32
  },
  "payoutAmount": {
    "currency": "EUR",
    "amount": 60.15
  },
  "payoutTransactionID": {
    "epTransactionID": 281474990733691,
    "merchantTransactionID": "ccttfx01g"
  },
  "epBankID": 9670420,
  "reason": " Account Address invalid . BE04",
  "reasonID": 111
}
```
For further information on [Reason codes](#/http/guides/reason-codes).

#### Payment Sent event
A notification is sent when a batch is executed.

```
{
  "notificationType": "PAYMENT_SENT",
  "epUserID": 3430090240848,
  "merchantUserIdentity": "1DBWSBQ1EPF78",
  "epTransactionID": 281475041370930,
  "timestamp": "2018-05-25T15:48:58.788+01:00",
  "managedMerchantIdentity": "Contracting Merchant User",
  "payoutTransactionID": {
    "epTransactionID": 281475041370930,
    "merchantTransactionID": "IntegrationTest:62537498"
  },
  "payoutRequestAmount": {
    "currency": "GBP",
    "amount": 145.32
  },
  "epBankID": 21068999
}
```