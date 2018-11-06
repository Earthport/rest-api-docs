## Getting started in sandbox

### Sandbox environment
The Sandbox environment is a complete replica of the Earthport production environment, supporting all of the same API endpoints. 
Applications must be tested against the Sandbox environment before being used in production.

### How to get access to sandbox
Currently you will need to contact Earthport (support@earthport.com). We will set you up and issue you with a unique client_id and secret.
In future, you will be able to register your details on this site and receive your client_id and secret once approved.

### Differences from production environment

* The Sandbox contains only test data and is completely separate from your production account.
* All API endpoints have a base URL of `https://api-sandbox.earthport.com` instead of `https://api.earthport.com`
* Actual money is **not** sent or received as part of test transactions.
* No compliance checks are performed against the test transactions such as automated AML checks.

Please note: **Real financial data should never be used in the Sandbox.**

Please read the suggested [Developer testing steps](1_0_0#/http/guides/introduction/Developer%20testing%20steps)