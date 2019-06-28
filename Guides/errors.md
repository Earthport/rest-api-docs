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
| **413**   | Request Entity Too Large. Earthport limits the request payload size to 100KB. |
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

A shortened error response can be returned when the error occurs in the API gateway layer rather than within the backend system. 

Examples could be an incorrectly formatted JSON request sent to the API endpoint or an empty request being sent to the endpoint.

```Javascript
{
    "timeOfFailure": "2019-01-11T15:32:09.519+00:00",
    "failureType": "validation",
    "shortMsg": "Generic validation failure",
    "longMsg": "Invalid json format: String contains control character."
}
```

### Validation error codes

| Code        | Description           |
| ---------------|-------------------------- |
| **10000**   | Generic validation failure. |
| **10001**   | Validation failure: Null SOAP input/payload received. |
| **10002**   | Schema validation failure during JAXB parsing. |
| **10004**   | Validation failure: unable to mediate supplied value. |
| **10006**   | Supplied account details do not match that of original user account. |
| **10007**   | Supplied service level is invalid. |
| **10206**   | Validation failure: entry not found. |
| **10306**   | Validation failure: duplicate exists. |
| **10318**   | Validation failure: invalid managed merchant. |
| **10404**   | Currency combination is not supported. |
| **10405**   | FX is not allowed. |
| **10406**   | Validation failure: Payout requested with Expired FxTicket. |
| **10407**   | Validation failure: FxTicket not found. |
| **10408**   | Validation failure: Fx quote between same currencies is not allowed. |
| **10409**   | Validation failure: FxTicket was already honoured by another Payout Request. |
| **10410**   | Validation failure: Beneficiary Bank Account specified does not exist. |
| **10411**   | Validation failure: Buy Currency is not same as Beneficiary Bank Account Currency. |
| **10412**   | Validation failure: Financial Transaction Search Service parameters not valid. |
| **10413**   | Validation failure: Financial Transaction not found. |
| **10414**   | The pagination parameters are incorrect. |
| **10415**   | Error during the processing of results of one of the Statement service query operations. |
| **10416**   | The pagination parameters passed in are incorrect. |
| **10417**   | Earthport transaction ID does not correlate to Merchant transaction ID. |
| **10418**   | The pagination parameters for FindUser are incorrect. |
| **10419**   | Error during the processing of results of the Find User service query operations. |
| **10420**   | The requested payout amount does not match that amount requested in the FX Ticket. |
| **10421**   | The parameters supplied in the request are invalid. |
| **10422**   | Unable to calculate a settlement calendar for the details supplied. |
| **10423**   | The supplied FX Ticket ID references a ticket which is not valid in this context. |
| **10424**   | Validation failure: Mandatory payout amount is missing for payout request with fx type of NO_FX. |
| **10425**   | Validation failure: Payout amount and beneficiary amount mismatch for payout request with fx type of NO_FX. |
| **10426**   | Validation failure: Payout amount or beneficiary amount information must be supplied. |
| **10427**   | Validation failure: Payout currency as part of beneficiary amount information must be supplied. |
| **10428**   | Validation failure: Supplied input details are not currently supported by the service. |
| **10429**   | Provision of both payout amount and beneficiary amount information must be accompanied by a valid FX ticket. |
| **10430**   | The amounts and rates provided with the payout request are invalid for the determined FX type. |
| **10431**   | The FX type is invalid for the given payout request input. |
| **10432**   | Unable to determine the FX type based on supplied amounts. |
| **11000**   | Validation failure: auto-batching route limit exceeded. |
| **11001**   | Validation failure: auto-batching daily beneficiary limit exceeded. |
| **11002**   | Validation failure: auto-batching route inactive. |
| **11003**   | Validation failure: auto-batching daily settlement limit exceeded. |
| **11004**   | Validation failure: Beneficiary Bank Van supplied in Payout Request is not valid for FXTicket specified. |
| **11005**   | Validation failure: Payout Currency in Payout Request is not valid for FXTicket specified. |
| **11006**   | Validation failure: Beneficiary Bank Currency in Payout Request is not valid for FXTicket specified. |
| **11007**   | No settlement route exists for this payout request. |
| **11008**   | Insufficient or invalid bank or payer/beneficiary identity data to settle this payout request. |
| **11009**   | No FX allowed and no settlement route exists for this payout request. |
| **11010**   | The password provided does not conform to minimum password strength requirements. |
| **11011**   | Illegal character data encountered while processing request. |
| **11012**   | No merchant balances to return. |
| **11013**   | The request has failed due to the VAN used for payout being in a closed state. |
| **11014**   | The request has failed due to the Beneficiary Bank account used for payout being inactive. |
| **11015**   | The request has failed as the virtual account type is not permitted. |
| **11016**   | Reset User service call failed. |
| **11017**   | No password was supplied. |
| **11018**   | No confirmation password was supplied. |
| **11019**   | The password and confirmation password do not match. |
| **11020**   | No user PIN was supplied. |
| **11021**   | The user PIN supplied was not of the required length. |
| **11022**   | The user PIN supplied has a missing value. |
| **11023**   | No confirmation PIN was supplied. |
| **11024**   | The PIN and confirmation PIN do not match. |
| **11025**   | Payout request would result in a zero or negative amount. |
| **11026**   | The Payout does not match any BulkFxDetails contained in the BulkFxTicket referenced. |
| **11027**   | Supplied FXTicket is invalid for this merchant. |
| **11028**   | No settlement route exists matching the request parameters. |
| **11029**   | Payout instruction with specified transaction id or merchant transaction reference not found. |
| **11030**   | Invalid State Transition. |
| **11031**   | Transaction not in a cancellable state. |
| **11032**   | Validation failure: Beneficiary Bank has not been set for FX Ticket. |
| **11033**   | Cancellation Request received for a transaction that is already pending to be cancelled. A refund notification will be issued if and when this transaction is successfully cancelled. |
| **11034**   | Unbatching rules prevent payment from being dispatched individually. |
| **11035**   | Unbatching rules have removed payment from batch during execution. |
| **11036**   | No route has been assinged for this payment. |
| **12000**   | Beneficiary Bank Account failed validation process. |
| **12001**   | Country supplied is not valid. |
| **12002**   | Beneficiary Bank Account country code has not been supplied. |
| **12003**   | Beneficiary Bank Account IBAN supplied implies a country different than the country code supplied. |
| **12004**   | Insufficient data supplied. The getBeneficiaryBankAccountRequiredData service should be called to discover the necessary data. Please contact customer support for more info. |
| **12005**   | Bank validation failed during payout request. Please re-register this bank account. |
| **12006**   | Payout instruction currency differs from selected SEG account currency. |
| **12007**   | Not enough details to register Beneficiary Bank Account. |
| **12011**   | An invalid currency code has been supplied. |
| **12012**   | Beneficiary Bank Account currency has not been supplied. |
| **12013**   | Currency code is not a valid ISO 3-char currency code. |
| **12014**   | Country code is not a valid ISO 2-char country code. |
| **12021**   | Beneficiary Bank Account Description not supplied. |
| **12022**   | Beneficiary Bank Account Description supplied contains non-alphanumeric characters. |
| **12031**   | Beneficiary Bank Account Name not supplied. |
| **12032**   | Beneficiary Bank Account Name supplied is too long. |
| **12033**   | Beneficiary Bank Account Name supplied contains non-alphanumeric characters. |
| **12034**   | Invalid Beneficiary Bank Account Name supplied. |
| **12035**   | Local Bank Account Name supplied is too long. |
| **12036**   | Invalid Local Bank Account Name supplied. |
| **12037**   | Beneficiary Bank Account Name supplied is too short. |
| **12041**   | Beneficiary Bank Name not supplied. |
| **12042**   | Beneficiary Bank Account Bank Name supplied is too long. |
| **12043**   | Beneficiary Bank Name supplied contains non-alphanumeric characters. |
| **12044**   | Beneficiary Bank Name supplied is invalid. |
| **12045**   | Beneficiary bank data supplied is not valid Zengin characters. |
| **12046**   | Beneficiary Bank Account Bank Name supplied is too short. |
| **12051**   | Beneficiary Bank Account Bank Code has not been supplied and is required in the territory. |
| **12052**   | Beneficiary Bank Account Bank Code supplied is too short. |
| **12053**   | Beneficiary Bank Account Bank Code supplied is too long. |
| **12054**   | Beneficiary Bank Account Bank Code supplied contains non-alphanumeric characters. |
| **12055**   | Beneficiary Bank Account Bank Code supplied contains non-numeric characters. |
| **12056**   | Bank Code should not be supplied for this territory. |
| **12057**   | The supplied Bank Code contradicts the Bank Code derived by Earthport software. |
| **12058**   | The supplied bank Code is not valid. |
| **12059**   | The supplied bank code contradicts the supplied account number. |
| **12061**   | Beneficiary Bank Branch Code has not been supplied and is required in the territory. |
| **12062**   | Beneficiary Bank Account Bank Branch Code supplied is too short. |
| **12063**   | Beneficiary Bank Account Bank Branch Code supplied is too long. |
| **12064**   | Bank Branch Code supplied contains non-alphanumeric characters. |
| **12065**   | Beneficiary Bank Account Branch Code supplied contains non-numeric characters. |
| **12066**   | Bank Branch Code should not be supplied for this territory. |
| **12067**   | The supplied Bank Branch Code contradicts the Bank Branch Code derived by Earthport software. |
| **12068**   | The supplied branch code is not valid. |
| **12071**   | Beneficiary Bank Account clearing code is not valid. |
| **12072**   | Beneficiary Bank Account swift code supplied contradicts the bank identified by the supplied bank code. |
| **12073**   | Beneficiary Bank Account BIC supplied contradicts the bank identified by the supplied bank code. |
| **12081**   | Beneficiary Bank Account Number supplied is invalid. |
| **12082**   | Beneficiary Bank Account Number has not been supplied and is required in the territory. |
| **12083**   | Beneficiary Bank Account number supplied is too long. |
| **12084**   | Beneficiary Bank Account number supplied is too short. |
| **12085**   | Beneficiary Bank Account number supplied contains non-numeric characters. |
| **12086**   | Beneficiary Bank Account number supplied contains non-alphanumeric characters. |
| **12087**   | Beneficiary Bank Account Number prefix supplied is too long. |
| **12088**   | Beneficiary Bank Account Number prefix supplied is too short. |
| **12089**   | Beneficiary Bank Account Number prefix supplied contains non-numeric characters. |
| **12090**   | Beneficiary Bank Account Number prefix supplied contains non-alphanumeric characters. |
| **12091**   | Beneficiary Bank Account Number supplied has failed the modulus check. |
| **12092**   | Beneficiary Bank Account number suffix supplied is too long. |
| **12093**   | Beneficiary Bank Account number suffix supplied is too short. |
| **12094**   | Beneficiary Bank Account number suffix supplied contains non-numeric characters. |
| **12095**   | Beneficiary Bank Account number suffix supplied contains non-alphanumeric characters. |
| **12096**   | Invalid Beneficiary Bank Account number supplied. |
| **12097**   | Beneficiary Bank Account Type has not been supplied and is required in the territory. |
| **12098**   | Beneficiary Bank Account Type supplied is invalid. |
| **12099**   | Beneficiary Bank Account Type supplied contains non-alphanumeric characters. |
| **12101**   | Beneficiary Bank Account Holding Branch name has not been supplied. |
| **12102**   | Beneficiary Bank Account Holding Branch name supplied contains non-alphanumeric characters. |
| **12105**   | Beneficiary Bank Account Number Suffix has not been supplied and is required in the territory. |
| **12111**   | Beneficiary Bank Account BIC has not been supplied and is required in the territory. |
| **12112**   | Beneficiary Bank Account Swift BIC supplied is invalid. |
| **12113**   | BIC supplied contains non-alphanumeric characters. |
| **12114**   | Swift BIC supplied contains non-alphanumeric characters. |
| **12115**   | Bank branch not found on CB.Net lookup. |
| **12116**   | Beneficiary Bank Account BIC supplied is invalid. |
| **12117**   | Bank code not found on CB.Net lookup. |
| **12118**   | Beneficiary Bank Account Country does not match the BIC country. |
| **12119**   | Beneficiary Bank Account Country does not match the SWIFT BIC country. |
| **12120**   | Error during clearing lookup. |
| **12121**   | Beneficiary Bank Account IBAN has not been supplied and is required in the territory. |
| **12122**   | Beneficiary Bank Account IBAN supplied is too short. |
| **12123**   | Beneficiary Bank Account IBAN supplied is too long. |
| **12124**   | Beneficiary Bank Account IBAN country not recognised in Earthport software. |
| **12125**   | Beneficiary Bank Account IBAN supplied has failed the modulus check. |
| **12126**   | IBAN supplied contains non-alphanumeric characters. |
| **12127**   | The supplied IBAN contradicts the IBAN derived by Earthport software. |
| **12128**   | The supplied IBAN contradicts the supplied routing number. |
| **12129**   | The supplied IBAN contradicts the supplied account number. |
| **12130**   | Invalid Beneficiary Bank IBAN supplied. |
| **12131**   | Beneficiary identity consisting of givenNames and familyName must be supplied. |
| **12132**   | No user identity attributes provided. |
| **12133**   | EP user ID provided does not map to Merchant User ID provided. |
| **12134**   | Invalid EP user ID provided. |
| **12135**   | Invalid Merchant user ID provided. |
| **12136**   | Invalid identity token provided. |
| **12137**   | Invalid payer type provided. |
| **12138**   | Invalid payer identity provided. |
| **12139**   | The Beneficiary Identity is now invalid. |
| **12140**   | Invalid payout details provided. |
| **12141**   | Invalid beneficiary identity type provided. |
| **12142**   | Beneficiary Bank Account does not belong to the User ID Specified. |
| **12143**   | Supplied VAN does not belong to the calling merchant. |
| **12144**   | Supplied VAN refers to an inactive virtual account. |
| **12145**   | Supplied XML version attribute is invalid. |
| **12146**   | No beneficiary bank identity attributes provided. |
| **12147**   | EP bank ID provided does not map to Merchant bank ID provided. |
| **12148**   | Invalid EP bank ID provided. |
| **12149**   | Invalid Merchant bank ID provided. |
| **12150**   | No such territory profile exists for given merchant. |
| **12151**   | Error in Route Selection Criteria input parameters. |
| **12152**   | Beneficiary Bank Account Misc field 1 supplied is too long. |
| **12153**   | Beneficiary Bank Account Misc field 1 supplied is too short. |
| **12154**   | Beneficiary Bank Account misc field 1 supplied contains non-numeric characters. |
| **12155**   | Beneficiary Bank Account misc field 1 supplied contains non-alphanumeric characters. |
| **12156**   | Beneficiary Bank Account Misc field 2 supplied is too long. |
| **12157**   | Beneficiary Bank Account Misc field 2 supplied is too short. |
| **12158**   | Beneficiary Bank Account misc field 2 supplied contains non-numeric characters. |
| **12159**   | Beneficiary Bank Account misc field 2 supplied contains non-alphanumeric characters. |
| **12160**   | Beneficiary Bank Account Misc field 3 supplied is too long. |
| **12161**   | Beneficiary Bank Account Misc field 3 supplied is too short. |
| **12162**   | Beneficiary Bank Account misc field 3 supplied contains non-numeric characters. |
| **12163**   | Beneficiary Bank Account misc field 3 supplied contains non-alphanumeric characters. |
| **12164**   | Supplied VAN refers to a locked virtual account. |
| **12165**   | Supplied VAN refers to a virtual account that is closing. |
| **12166**   | Supplied VAN refers to a closed virtual account. |
| **12167**   | Supplied managed merchant identity does not match that of the calling merchant. |
| **12170**   | A value must be supplied for either the sellAmount or buyAmount request parameter. |
| **12171**   | BuyAmount and SellAmount have both been specified. |
| **12172**   | sellCurrency sand sellAmount have both been specified. |
| **12173**   | buyCurrency sand buyAmount have both been specified. |
| **12174**   | A value must be supplied for the sellCurrency request parameter. |
| **12175**   | A value must be supplied for the buyCurrency request parameter. |
| **12176**   | No FX rates found for the request parameters. |
| **12180**   | The merchant parent cannot be found. |
| **12181**   | The merchant parent would cause a cyclic inheritance. |
| **12182**   | No payer identity information specified. |
| **12183**   | The contracting merchant cannot be found. |
| **12184**   | System username already exists. |
| **12185**   | No system user found for a contracting merchant. |
| **12186**   | The managed merchant cannot be found. |
| **12187**   | The system user cannot be found. |
| **12188**   | No account is configured for the merchant parent. |
| **12189**   | A value for username is missing. |
| **12190**   | At least one SystemUserGroup should be specified for a SystemUser. |
| **12191**   | Cannot edit a user that belongs to a different Merchant. |
| **12192**   | No identity information for this user. |
| **12193**   | Payer identity information specified is invalid. |
| **12194**   | Given payerType does not support provision of payer identity information. |
| **12195**   | Merchant deactivation is not allowed. |
| **12196**   | Refunds strategy change is not allowed. |
| **12197**   | Maximum date range for query has been exceeded. |
| **12201**   | Beneficiary Bank Account Sort Code supplied is too long. |
| **12202**   | Beneficiary Bank Account Sort Code supplied is too short. |
| **12203**   | Beneficiary Bank Account Sort Code supplied contains non-numeric characters. |
| **12204**   | Beneficiary Bank Account Sort Code supplied contains non-alphanumeric characters. |
| **12205**   | Beneficiary Bank Account Sort Code has not been supplied. |
| **12206**   | Beneficiary Bank Account Sort Code supplied is not eligible for UK Faster Payments. |
| **12207**   | Beneficiary Bank Account Sort Code is invalid. |
| **12210**   | Beneficiary Bank Account Aba Routing Number is invalid. |
| **12211**   | Beneficiary Bank Account Aba Routing Number supplied is too long. |
| **12212**   | Beneficiary Bank Account Aba Routing Number supplied is too short. |
| **12213**   | Beneficiary Bank Account Aba Routing Number supplied contains non-numeric characters. |
| **12214**   | Beneficiary Bank Account Aba Routing Number supplied contains non-alphanumeric characters. |
| **12215**   | Beneficiary Bank Account Aba Routing Number has not been supplied. |
| **12216**   | An aba routing number has been supplied which contradicts the one derived from this account. |
| **12217**   | Beneficiary Bank Account Fedwire Code supplied is too long. |
| **12218**   | Beneficiary Bank Account Fedwire Code supplied is too short. |
| **12219**   | Beneficiary Bank Account Fedwire Code supplied contains non-numeric characters. |
| **12220**   | Beneficiary Bank Account Fedwire Code supplied contains non-alphanumeric characters. |
| **12221**   | Both an aba routing number and a Fedwire code have been supplied which contradict each other. |
| **12222**   | Invalid fedwire code. |
| **12231**   | A balance for the currency and account requested does not exist. |
| **12250**   | The Deposit Reference FX Ticket ID supplied has not been recognised. |
| **12251**   | The Deposit Reference supplied does not conform to the required syntax format. |
| **12252**   | The Deposit Reference supplied contains an unrecognised merchant prefix. |
| **12253**   | The Add Deposit Reference service is only available to contracting merchants. |
| **12254**   | The Add Deposit Reference service stipulates all deposit references must be unique. The supplied deposit reference already exists. |
| **12256**   | EPS deposit reference does not exist. |
| **12257**   | EPS invalid VAN failure. |
| **12262**   | Unexpected sender details format. |
| **12263**   | Unexpected currency code format. |
| **12264**   | Unexpected settlement amount format. |
| **12265**   | Unexpected value date format. |
| **12266**   | The supplied IBAN contradicts the supplied account number prefix. |
| **12275**   | Invalid dual approval approver. |
| **12276**   | The batch contains payout instructions awaiting dual approval. |
| **12277**   | Reached limit of number of routes that can be exported - Please narrow your criteria. |
| **12278**   | The batch contains expected payout debits awaiting dual approval. |
| **12351**   | The birth information provided is not valid. |
| **12352**   | The dates provided for the identification are not valid. |
| **12353**   | The address supplied as part of the identity information is not valid. |
| **12354**   | The additional data key supplied is not known. |
| **12355**   | The identification type supplied is not valid. |
| **12356**   | The identification type is not provided. |
| **12357**   | Identification number of National ID Card is too long. |
| **12358**   | Identification number of National ID Card is not numeric. |
| **12359**   | Identification number of National ID Card is not valid. |
| **12360**   | Email address provided is not valid. |
| **12361**   | Country used in address is not allowed here. |
| **12362**   | Country used in identity is not allowed here. |
| **12450**   | The swift fields provided are not sufficient for bank registration. The <key> within the validation failure should identify which fields are missing. |
| **12451**   | Beneficiary Bank Account Intermediary Swift BIC supplied is invalid. |
| **12551**   | No bank partner reference found for supplied bank account. |
| **13000**   | The supplied username could not be found. |
| **13001**   | The password is incorrect for the supplied username. |
| **13002**   | The end user account is locked. |
| **13003**   | The PIN is incorrect for the supplied username. |
| **13004**   | The end user must belong to the Approver group for dual authentication. |
| **13005**   | The approver user account is locked. |
| **13006**   | The end user's account is not active. |
| **13007**   | The new PIN value must be different to the current PIN value. |
| **13008**   | The approver user does not belong to the same merchant as the approvee. |
| **13501**   | The supplied merchant fee does contain the payment currency. |
| **13502**   | The supplied merchant fee is a duplicate. |
| **13503**   | The supplied merchant fee does contain the actual fee. |
| **13504**   | The supplied merchant fee cannot be a negative amount. |
| **13505**   | The supplied merchant fee belongs to another merchant. |
| **13506**   | The supplied merchant fx rate does not have the currency set. |
| **13507**   | The supplied merchant fx rate is not set. |
| **13508**   | The supplied merchant fx rate is invalid due to either being zero or a negative amount. |
| **14500**   | Number of items in batch does not correspond to batch control total. |
| **14501**   | At least one item failed validation when validation errors are not allowed. |
| **14502**   | More than the allowed number of items failed validation. |
| **14503**   | Next item in batch cannot be read. |
| **14504**   | Input file does not follow the expected format. |
| **14505**   | The XML of the item is invalid or does not comply with the published XML schema definition for this service. |
| **14506**   | A failure occurred within the payload processor and ABIF file processing cannot continue. |
| **14507**   | The input file is empty. |
| **14508**   | A payload item failed validation. |
| **14509**   | Input filename has illegal format. |
| **14510**   | Mandatory value is missing. |
| **14511**   | Invalid date of birth. |
| **14512**   | Invalid date interval. |
| **14513**   | Value contains non alpha-numeric characters. |
| **14514**   | Value contains non alpha (a-z, A-Z) characters. |
| **14515**   | Value is not binary. |
| **14516**   | Value exceeds the maximum length allowed. |
| **14517**   | Value shorter than the minimum length allowed. |
| **14518**   | Value is not numeric. |
| **14519**   | At least one specification must be satisfied. |
| **14520**   | Only one specification must be satisfied. |
| **14521**   | Beneficiary identity information specified is invalid. |
| **14522**   | The Tax Code is invalid. |
| **14523**   | The additional identity data block contains more than one item of the same type. |
| **14524**   | The additional identity data block contains an invalid item. |
| **14525**   | A valid purpose of payment must be supplied. |
| **14526**   | The Brazilian Individual Tax Identification Number 'CPF' is invalid. |
| **14527**   | The Brazilian Federal Employers Identification Number 'CNPJ' is invalid. |
| **14528**   | Value contains non-supported characters. |
| **14529**   | At least one of the additional data items must be supplied. |
| **14530**   | Mandatory additional data item for key is missing. |
| **14531**   | Value has incorrect length or format, or contains invalid characters. |
| **14532**   | A default purpose of payment was supplied, but appeared to be incorrect. |
| **14533**   | A purpose of payment has not been supplied. |
| **14534**   | Company Registration Number is invalid. |
| **14535**   | ABIF batch file with invalid namespace version for submitBatch. |
| **14551**   | The item is a debit. |
| **14552**   | Invalid originator name. |
| **14553**   | Invalid beneficiary name. |
| **14554**   | Invalid originator country. |
| **14555**   | Invalid receiver country. |
| **14556**   | Identity flag missing for item. |
| **14557**   | Invalid item in input file. |
| **14558**   | Variable to fix fx not allowed. |
| **14559**   | Invalid releaseDateTime. |
| **14560**   | Invalid offsetMinutes. |
| **14561**   | Unstructured identity information specified is invalid. |
| **14562**   | Mandatory identity data items are missing. |
| **14563**   | The unstructured identity data block contains more than one item of the same type. |
| **14564**   | The unstructured identity data block contains an invalid item. |
| **14565**   | Invalid CNAPS provided. |
| **14566**   | There is no such BIC in BankPartnerReference table. |
| **14567**   | There is no such SWIFT BIC in BankPartnerReference table. |
| **14568**   | There is no such BIC or SWIFT BIC in BankPartnerReference table. |
| **14569**   | BIC or SWIFT BIC is not supplied. |
| **14570**   | Bank data insufficient - Please see EP documentation. |
| **14571**   | BIC or SWIFT BIC is not present in trusted list. |
| **15000**   | Wallet already registered with this merchant wallet id. |
| **15001**   | Settlement to beneficiary wallet is not supported. |
| **15002**   | Validation failure: Supplied input details are invalid. |
| **15003**   | Insufficient Merchant Liquidity. |
| **15004**   | Supplied bank and branch codes belong to different banks. |
| **15005**   | Validation failure: unknown provider name supplied. |
| **15006**   | Validation failure: you are not authorised to call this service. |
| **17000**   | Beneficiary Bank Account Intermediary Account supplied field is too long. |
| **17001**   | Beneficiary Bank Account Intermediary Account supplied field contains not supported characters. Supported is alphanumeric / - ? : ( ) . , ' + CrLf Space. |
| **17100**   | Beneficiary Bank Account Number and Sort Code mismatch. |