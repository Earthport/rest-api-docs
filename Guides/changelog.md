All notable changes to both the APIs and the documentation will be documented in this file. The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.1.2] - 2020-11-30
### Added
- Field "dateSentToBank" to 'Payout Transaction' structure page.

### Changed
- Data Type to 'Object' for "amountRefundedByBank", "amountRefundedToCustomer", "reason" and "originalPayoutTransaction" fields within 'Refund Transaction' structure page. 
- Data Type to 'Object' for "refundPayoutID" field within 'Payout Transaction' structure page. 

## [1.1.1] - 2020-11-11
### Added
- Fields such as "refundPayoutID" and "fxExecutedDetail" to 'Payout Transaction' structure page.
- Fields such as "fxExecutedDetail", "amountRefundedByBank", "amountRefundedToCustomer", "reason" and "originalPayoutTransaction" to 'Refund Transaction' structure page.
- "description" field to 'Journal Transaction' and 'Merchant Liquidity Movement Transaction' structure page.

### Changed
- "Key" / "Value" fields to lowercase for 'Unstructured Identity' structure page.

### Removed
- "description" field from 'Financial Transaction' structure page. 

## [1.1.0] - 2020-09-28
### Changed
- Description within 'Additional Data' structure page.

## [1.0.9] - 2020-08-20
### Added
- Fields such as "feeValue", "fxMethodExpected" and "fxRate" to 'Payments Registered Beneficiary Create Response' structure page.

### Changed
- Description within 'Beneficiary Bank Account Create Request' structure page.
- Description for 'payerIdentity' field within 'Users Create or Validate Request'.

## [1.0.8] - 2020-08-07
### Added
- "Unstructured Identity Examples" section under Guides. 
- "Unstructured Key Names" page under Enumerations.

### Changed
- Images within the 'Introduction' guide section to match API Documentation.
- Description of 'Key' field as a link to attach "Unstructured Key Names" enumerator within 'Unstructured Identity' page.

## [1.0.7] - 2020-03-19
### Added
- "Payment overview" section under Guides. 

## [1.0.6] - 2019-11-28
### Changed
- Changed the spelling of 'Respone' to 'Response' within the structure 'Payments Registered Beneficiary Create Response' 

## [1.0.5] - 2019-11-26
### Changed
- Changed the "IgnoreIfNullJson" field value from 'false' to 'true' within the API settings.
- Changed the field name 'Key' and 'Value' within the 'Additional Data' page to lowercase in the beginning located in the 'HTTP' section. 

## [1.0.4] - 2019-09-06
### Changed
- Fixed an error that was caused when supplying an integer, instead of a string, into the key values of "Add bank account" API. This was changed so that only a string will be accepted for all value fields. 
- Fixed an error that was caused when supplying long account numbers (ie. Morocco account numbers can be up to 24 digits), where a client provided the example "190170211401005132000877", this was then appearing in scientific notation (eg. 1.2345678901234568e+39) when using "Get bank account" API. This has been changed so that it returns as a string without losing any digits.

## [1.0.3] - 2019-06-06
### Added
- "Reason codes" section under Guides. 

### Changed 
- Added brief description for each Webhook event type under "Webhooks" section. 
- Added "Reason codes" link under "Webhooks" section.
- Added "Validation error codes" under "Errors" section. 

## [1.0.2] - 2019-03-27
### Changed
- Fixed OAS spec and client SDKs. The structure BeneficiaryBankAccountFieldsList was changed to contain an array/list of BeneficiaryBankAccountField objects rather than a single BeneficiaryBankAccountField object.

## [1.0.1] - 2019-02-26
### Changed
- Fixed authentication endpoint so that it returns a valid OAuth token type. token_type is now "Bearer" rather than "BearerToken".
- Renamed managedMerchantIdentity to managedMerchantName in [User](#/http/models/structures/user) to be consistent with other endpoints.
- Added max length for VAN(13)
- Added max length for managedMerchantName(30)
- Added max length for merchantUserID(100)
- Added max length for merchantBankID(100)
- Added max length for merchantTransactionID(255)
- Added optional FX Fees as part of payout response
- Descoped the locale field on the get meta service