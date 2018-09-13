## Idempotency

The API supports [idempotency](https://en.wikipedia.org/wiki/Idempotence) for safely retrying requests without accidentally performing the same operation twice. This is useful when an API call is disrupted in transit and you do not receive a response. For example, if a request to create a payment fails due to a network connection error, you can retry the request with the same merchantTransactionID to guarantee that only a single payment is created.

Rather than using a separate idempotency key, we instead require a specific field per service to be unique.

Multiple POSTs where this field contains the same value won't result in multiple resources being created. In fact, an error will be returned indicating a duplicate value.

| Service                                               | Idempotent field           |
| ----------------------------------------------- |---------------------------------- |
| Create User                                      | merchantUserID             |
| Add Beneficiary Bank Account      | merchantBankID            |
| Payout Request                                | merchantTransactionID |