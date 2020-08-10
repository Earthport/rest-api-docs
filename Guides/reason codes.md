This is also referred to as the ReasonID. A notification is sent when a Rejected Payout event or a Refund event occurs, here is the full list of reason codes with the corresponding reason message. 

### Rejected Payout codes

| ReasonID | Reason |  
| ----------|----------- |                            
**1**|Invalid BIC code |
**2**|Invalid routing code |
**3**|Invalid IBAN |
**4**|Invalid A/C no. |
**5**|BIC and IBAN do not match |
**6**|IBAN and country code do not match | 
**7**|No A/C name quoted |
**8**|No A/C no. quoted |
**9**|No bank name quoted |
**10**|Too small to process |
**11**|Destination country is not supported |
**12**|Beneficiary details contain invalid characters | 
**13**|Third party payments not supported by Earthport |
**14**|Recall requested by Remitter |
**34**|Our bank is unable to make electronic payments to the beneficiary bank |
**35**|Invalid Bank Code |
**36**|Invalid Branch Code |
**37**|BIC & Bank Code Mismatch |
**38**|BIC & Branch Code Mismatch |
**39**|Bank name & Branch Code Mismatch |
**40**|Bank name & Bank code Mismatch |
**41**|Bank name & IBAN Mismatch |
**42**|Bank name & BIC Mismatch |
**43**|Account Number & IBAN Mismatch |
**44**|Bank Code & IBAN Mismatch |
**45**|Branch Code & IBAN Mismatch |
**46**|Reference contains invalid characters |
**47**|Beneficiary name contains invalid characters |
**48**|Invalid Country Code |
**59**|KYC information not received so bank has returned payment |
**60**|BIC code and Country code mismatch |
**61**|No valid correspondence details |
**62**|Beneficiary A/c is in a different currency to payment |
**67**|Bank cannot process |
**68**|Beneficiary account closed |
**69**|Beneficiary bank cannot FX funds |
**70**|Beneficiary has refused credit |
**71**|Beneficiary name and A/C no. do not match |
**73**|Invalid Bank name |
**74**|Invalid Beneficiary name |
**75**|Non-Transaction Account |
**76**|Not enough information on the beneficiary to process |
**77**|Reason Unspecified by the bank |
**78**|No IBAN Quoted |
**96**|Forbidden Transaction |
**97**|Blocked bene account |
**98**|Beneficiary deceased |
**99**|Not allowed |
**100**|Duplicate Payment  - AM05 |
**101**|Account Address invalid . BE04 |
**102**|Regulatory reason . RR01-04 |
**105**|Credit transfer forbidden on this type of account (eg.  savings)-AG01 |
**112**|Regulatory reason . RR01-04 |
**116**|Invalid Beneficiary Details |
**118**|Beneficiary Bank Unable to Apply |
**119**|Incomplete Details |
**123**|Beneficiary bank request |
**124**|Invalid Payer Details |
**126**|Invalid Beneficiary Birth Country |
**129**|Missing Payer Date of Birth |
**130**|Missing Payer Country of Birth |
**134**|Invalid branch name |
**135**|No account or cannot locate |
**138**|Maximum annual turnover in beneficiary account exceeded |
**141**|Compliance Reasons |
**143**|Exceeds max payout limit |
**145**|Invalid Beneficiary Details |
**146**|Insufficient funds |
**147**|Wrong/Invalid CPF number |
**148**|Beneficiary bank not SWIFT connected |
**150**|Invalid Tax Number |
**152**|Invalid or No VO code |
**154**|Beneficiary bank can not accept faster payments |
**156**|Sort code does not accept faster payments |
**160**|Daily Limit of Beneficiary Account Exceeded |
**162**|Beneficiary account invalid for BACs payments |
**163**|Exceeds EP risk appetite |
**164**|ATB initiated recall |
**165**|ATB client initiated recall |
**166**|Remitter Country Code Does not match with address |
**168**|KID ref not supplied |
**170**|Invalid National ID Number |
**172**|Invalid or no BGC/OCR reference |
**174**|Invalid or No BULSTAT |
**176**|Invalid Sort Code |
**178**|Charity donation not allowed |
**179**|No Purpose of Payment |
**181**|Beneficiary account unable to accept electronic transfers |
**183**|Account Name too long |
**185**|Payments to Legal Entities not allowed |
**187**|Beneficiary bank not reachable via SEPA |
**190**|Incorrect modal code |
**193**|RUT and Account mismatch or invalid |
**194**|RUT incorrect |
**195**|Invalid RUC |
**199**|Invalid Identity Information - CC, CE, NIT or PASS |
**201**|Invalid Identity Information – CCI |
**202**|Invalid Identity Information - CUIT, CUIL or CBU |
**204**|Payment has not been mandated |

### Refund codes

| ReasonID | Reason |  
| ----------|----------- | 
**15**|Invalid BIC code | 
**16**|Invalid routing code |
**17**|Invalid IBAN |
**18**|Invalid A/C no. |
**19**|BIC and IBAN do not match |
**20**|IBAN and country code do not match |
**21**|No A/C name quoted |
**22**|No A/C no. quoted |
**23**|No bank name quoted |
**24**|Beneficiary name and A/C no. do not match. |
**25**|Beneficiary has refused credit |
**26**|Our bank is unable to make electronic payments to the beneficiary bank |
**27**|Beneficiary account closed |
**28**|Recall requested by Remitter |
**49**|Invalid Bank Code |
**50**|Invalid Branch Code |
**51**|Invalid Bank name |
**52**|Invalid Beneficiary name |
**54**|Non-Transaction Account |
**55**|Bank cannot process |
**56**|Beneficiary bank cannot FX funds |
**57**|Reason Unspecified by the bank |
**58**|Too small to process |
**63**|KYC information not received so bank has returned payment |
**64**|BIC code and Country code mismatch |
**65**|No valid correspondence details |
**66**|Beneficiary A/c is in a different currency to payment |
**79**|Account Number & IBAN Mismatch |
**80**|BIC & Bank Code Mismatch |
**81**|BIC & Branch Code Mismatch |
**82**|Bank Code & IBAN Mismatch |
**83**|Bank name & BIC Mismatch |
**84**|Bank name & IBAN Mismatch |
**85**|Bank name & Bank code Mismatch |
**86**|Bank name & Branch Code Mismatch |
**87**|Beneficiary details contain invalid characters |
**88**|Beneficiary name contains invalid characters |
**89**|Branch Code & IBAN Mismatch |
**91**|Reference contains invalid characters |
**93**|Not enough information on the beneficiary to process |
**95**|No IBAN Quoted |
**107**|Blocked bene account |
**108**|Beneficiary deceased |
**109**|Not allowed |
**110**|Duplicate Payment  - AM05 |
**111**|Account Address invalid . BE04 |
**115**|Credit transfer forbidden on this type of account (eg.  savings)-AG01 |
**120**|Beneficiary Bank Unable to Apply |
**121**|Incomplete Details |
**122**|Beneficiary bank request |
**125**|Invalid Payer Details |
**127**|Invalid Beneficiary Birth Country |
**131**|Debtors address is missing or incorrect |
**132**|Maximum annual turnover in beneficiary account exceeded |
**133**|Dormant Account |
**136**|No account or cannot locate |
**144**|Invalid Beneficiary Details |
**149**|Beneficiary bank not SWIFT connected |
**151**|Invalid Tax Number |
**153**|Invalid or No VO code |
**155**|Missing Payment Reason |
**157**|Wrong/Invalid CPF number |
**158**|Invalid branch name |
**159**|Daily Limit of Beneficiary Account Exceeded |
**161**|Beneficiary account invalid for BACs payments |
**167**|KID ref not supplied |
**169**|Invalid National ID Number |
**171**|Invalid or no BGC/OCR reference |
**173**|Invalid or No BULSTAT |
**175**|Invalid Sort Code |
**177**|Charity donation not allowed |
**180**|Beneficiary account unable to accept electronic transfers |
**182**|Account Name too long |
**184**|Payments to Legal Entities not allowed |
**186**|Beneficiary bank not reachable via SEPA |
**189**|Incorrect modal code |
**191**|RUT and Account mismatch or invalid |
**192**|RUT incorrect |
**197**|MD06 Disputed authorized transaction |
**198**|Invalid Identity Information - CC, CE, NIT or PASS |
**200**|Invalid Identity Information – CCI |
**203**|Payment has not been mandated

For more information, refer to [Rejected Payout event](#/http/guides/webhooks/webhook-event-types/rejected-payout-event) and [Refund event](#/http/guides/webhooks/webhook-event-types/refund-event) under webhooks.