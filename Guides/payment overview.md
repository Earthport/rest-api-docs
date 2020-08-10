The Visa Payments Limited platform enables bank transfer remitting capability to bank accounts in multiple countries and territories. The system supports multiple currencies and enables foreign exchange when and if required - it also facilitates collection of funds. The access to each specific territory is configured for each client and changes or additions to this can be requested via the Account Manager.

![alt text](https://raw.githubusercontent.com/Earthport/rest-api-docs/master/images/overview_of_payments_limited_solution.png)

### End-to-end process flow
To access the Global ACH network the client has multiple options. The Client API allows full integration with web services for a synchronous and interactive user experience, as the services can be integrated with the client’s own system such that the user sees them as being part of the client’s overall offering - more details can be found under the [Payment Flows](#/http/guides/payment-flows) section. 

The diagrams illustrate the minimum flow required, which involves 3 steps:
* registering a user
* registering a beneficiary
* creating the transaction
It also offers variations of such flow including functionality such as dynamic screens, instant FX, etc.

### Payment Management
Within the platform all transactions are tracked and managed through the use of virtual accounts. A virtual account (VAN) is a system ledger that records the debit and credit transactions processed on behalf of the account owner. It is capable of holding balances in multiple currencies and each balance reflects the real-world funds being managed on behalf of the account owner. There are two types of accounts, those created on behalf of **users** for payment and collection transaction tracking purposes and those created for **clients** for payment management purposes. The accounts associated to clients are often referred to as “Central Accounts”. Clients may be referred to by other titles but are essentially the client which holds the contract arrangement with Visa Payments Limited for the provision of services.

##### User Definitions
A user can be identified as
1. The remitter of a payment made to a beneficiary associated to that user.
2. The remitter of a payment to a Contracting Merchant or Managed Merchant.

#### Central Virtual Accounts
In order to manage payments in the platform, the client is assigned a central account through which the funding of all transactions will ultimately flow. There may be a direct link between the client and the user, or there may be an additional layer between “Client” and the beneficiary (or remitter of a collection), and this is explained in the [Client Aggregation Model](#/http/guides/payment-overview/the-client-aggregation-model) section.

The client account is the source of funds for satisfying payment remittance requests and as such must have sufficient liquidity to cover the requested payment total. When the central account does not hold sufficient funds in the specific currency in order to cover payment requests such payments are still accepted but kept on hold until sufficient funds are received. The central account balance reflects the client’s real-world funding position and can be inspected using reports provided in the online Merchant Administration System (MAS) or via the API services Get Balance and Get Statement.

#### User Virtual Accounts
In order for transactions to / from a user to be identified, each user is allocated a unique Virtual Account Number (VAN) and this can be used to provide an audit trail for all payments / collections processed to or from user. The user’s accounts do not hold any actual balance. The client must maintain the association between a user’s virtual account and whatever additional user records they retain on their own system.

### The Client Aggregation Model
Every client that contracts directly with Visa Payments Limited and is configured in the system as a “Contracting Merchant”. 

#### Managed Merchants
The platform user account model also supports the concept of an optional hierarchy of client accounts or Merchant accounts. This is where the contracting organisation is able to sub-divide their account structure into logical groupings.

Typically, this structure is used by organisations that manage multiple business areas but have one back office system co-coordinating the payments processed. Consider the diagram below. The additional client accounts established in such a hierarchy are known as “**Managed Merchants**”.

![alt text](https://raw.githubusercontent.com/Earthport/rest-api-docs/master/images/payments_limited_client_hierarchy.PNG)

#### The Levels
1. Contracting Merchant – The entity with which Visa Payments Limited holds a contract to provide Payment Services.
2. Managed Merchant – These can be subsidiary companies or business areas of the Contracting Merchant. These have autonomous control of those users which are attached to each account. These are optional for Contracting Clients.
3. User – These are individual accounts from which payments or collections can be transacted. Each user can hold any number of accounts in any of the currencies supported by Visa Payments Limited.
4. Beneficiary – This is the detail of a beneficiary to which a user is entitled to make payments. An unlimited number of beneficiaries may be applied to each user.

Each Contracting or Managed Merchant can be assigned its own set of API credentials so that the Managed Merchant account can be accessed from within Managed Merchant’s own system. If a user account is created using a Managed Merchant’s API credentials then the account will be created under this managed merchant, this applies also to payments and collections.

The Contracting Merchant can access a Managed Merchant’s account and customer accounts by specifying the “**ManagedMerchantIdentity**” assigned to a specific Managed Merchant where applicable. A Managed Merchant cannot access any information of either the Contracting Merchant or any other Managed Merchant.

A “Managed Merchant” account can be configured to transact payments, deposits, rejections and returns notifications to its own URLs. Therefore, “Managed Merchant” integration can operate independently of the Contracting Merchant’s system. Further information about these processes can be found in the appropriate payment or collections section.

“Managed Merchant” accounts are set-up by Visa Payments Limited administrators upon the request of a Contracted Merchant.