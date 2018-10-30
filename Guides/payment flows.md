## Payment flows
In a nutshell, the payments flow can be summarised as follows:-

![alt text](https://raw.githubusercontent.com/Earthport/rest-api-docs/master/images/payment_flow.PNG "Payment flow")

The key elements to be captured are:
* Payer information - identity is the main requirement
* Beneficiary information - here we need to capture the identity but also the bank account details, of course, so we know where to deliver the money!
* Payment details - amount, currency, additional references, etc. that are related to this specific payment

Below are some of the most common implementations of this logic in our platform:

* Payment service flow (minimum)
* **Recommended** Payment service flow (with dynamic screens)
* Payment service flow (with hardcoded screens)

### Payment service flow (minimum)

The flow below lists the *minimum* service calls required to generate a payment:

| # | API call | Notes |
| - | ----------- | --------- |
| 1 | POST /users	             | Registers the user, i.e. your customer who is the payer of the transaction. Returns epUserID identifier for the user created |
| 2 | POST /users/{epUserID}/bank-accounts	| Registers the beneficiary, i.e. who will receive the payment. Returns epBankID for the beneficiary record created (includes both bank account details and beneficiary identity) |
| 3 | POST /users/{epUserID}/bank-accounts/{epBankID}/payments	| Creates the payment instruction from the payer to the beneficiary. Returns epTransactionID for the transaction created |

As you can see, they need to be run in this specific order, given that each call requires the output from the previous call. In other words, a beneficiary is linked to a user and a payment is linked to both the user and the beneficiary. 
Below is a diagram that shows a proposed flow of actions on your application triggering / processing the response of these services:

![alt text](https://cdn.rawgit.com/Earthport/rest-api-docs/master/images/RestAPI-Payments-Granular-minimum.svg "Payment service (minimum flow)")

### Recommended Payment service flow (with dynamic screens)

The flow below includes additional optional services recommended to improve the customer experience by providing tailored screens that prompt only for the required information:

| # | API call | Notes |
| - | ----------- | --------- |
| 1 | GET /payments/meta	| Returns the metadata to create dynamic logic for payer and beneficiary details acquisition |
| 2 | POST /users | Registers the user, i.e. your customer who is the payer of the transaction Returns epUserID identifier for the user created |
| 3 | POST /users/{epUserID}/bank-accounts | Registers the beneficiary, i.e. who will receive the payment Returns epBankID for the beneficiary record created (includes both bank account details and beneficiary identity) |
| 4 | GET /users/{epUserID}/bank-accounts/{epBankID}/payments/meta | Returns the metadata to create dynamic logic for payment details acquisition |
| 5 | POST /users/{epUserID}/bank-accounts/{epBankID}/payments | Creates the payment instruction from the payer to the beneficiary Returns epTransactionID for the transaction created |

There are two metadata calls. The first one takes only country and currency and returns the elements related to the identity of payer and beneficiary, as well as the specific bank account requirements for that route. The second one, relies on pre-registered payer and beneficiary and returns specific payment data that is required for that combination of identities and route. For example, the Purpose of Payment may be required if the beneficiary is a Legal Entity but not for remittance transactions (where both payer and beneficiary are individuals).
Below is a diagram that shows a proposed flow of actions on your application triggering / processing the response of these services:

![alt text](https://cdn.rawgit.com/Earthport/rest-api-docs/master/images/RestAPI-Payments-Granular-dynamic.svg "Payment service (recommended flow)")

### Payment service flow (with hardcoded screens)

Using the metadata requests to create dynamic screens is our recommended option as it ensures your system is always up-to-date with the latest updates made in our platform without the maintenance overhead. However, we understand this is not always possible or may need to be deferred to a later phase. In that event, an alternative to provide similar customer experience is to hardcode all the data requirements in your app and use a flow like the one below:

![alt text](https://cdn.rawgit.com/Earthport/rest-api-docs/master/images/RestAPI-Payments-Granular-hardcoded.svg "Payment service (hardcoded screen flow)")