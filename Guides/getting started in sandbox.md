### Sandbox environment
The Sandbox environment is a complete replica of the Visa Payments Limited production environment - it supports all of the same API endpoints. 
Applications **must** be tested against the Sandbox environment before being used in production.

### How to get access to sandbox
Currently you will need to contact Visa Payments Limited (api-support@earthport.com), from there we can set you up by issuing you with a unique client_id and secret.
In future, you will be able to register your details on this site and receive your client_id and secret once approved.

### Differences from production environment

* The Sandbox contains only test data and is completely separate from your production account.
* All API endpoints have a base URL of `https://api-sandbox.earthport.com` instead of `https://api.earthport.com`
* Actual money is **not** sent or received as part of test transactions.
* No compliance checks are performed against the test transactions such as automated AML checks.

**Warning** - Real financial data should never be used in the Sandbox.

Please read the suggested [Developer testing steps](#/http/guides/introduction)