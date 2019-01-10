### Time zones / dates

All timestamps are formatted as [ISO 8601 with timezone information](https://en.wikipedia.org/wiki/ISO_8601). For API calls that allow for a timestamp to be specified, we use that exact timestamp. These timestamps look something like 2014-02-27T15:05:06.123Z.

For endpoints that require dates, we expect a date string of the format YYYY-MM-DD, where an example would look like 2014-02-27.

### Currencies

Wherever an API contains a field referring to a currency then it requires a currency code. 

Earthport uses the [ISO 4217 3 letter currency code](https://en.wikipedia.org/wiki/ISO_4217). e.g. USD, GBP, EUR

### Countries

Where an API contains a field referring to a country then it requires a country code.

Earthport uses the [ISO 3166 2 letter country code](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2). e.g. GB, US, CH

### Amounts

The REST API represents financial amounts as decimals. However, Earthport's backend system converts this into a Monetary Amount class taking into account the number of decimal places for the specific currency and using a Java BigDecimal to handle floating point precision.

### Encoding

We expect all data that is sent to Earthport's APIs to be UTF-8 encoded.