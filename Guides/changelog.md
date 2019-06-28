All notable changes to both the APIs and the documentation will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

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
- Renamed managedMerchantIdentity to managedMerchantName in [User](https://docs.earthport.com/v/1_0_0#/http/models/structures/user) to be consistent with other endpoints.
- Added max length for VAN(13)
- Added max length for managedMerchantName(30)
- Added max length for merchantUserID(100)
- Added max length for merchantBankID(100)
- Added max length for merchantTransactionID(255)
- Added optional FX Fees as part of payout response
- Descoped the locale field on the get meta service