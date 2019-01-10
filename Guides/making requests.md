The API is only available over HTTPS. Any requests made using HTTP will fail to connect.

You will need to ensure you are using TLS v1.2 or higher.

### API host
| Environment   | Base URL                                             |
| -------------------- |---------------------------------------------------|
| Sandbox          | `https://api-sandbox.earthport.com`|
| Integration      | `https://api-integration.earthport.com`|
| Production      | `https://api.earthport.com`                 |

### Authentication and authorization
Once Earthport has issued you with your **client_id** and **secret** you can then use these to authenticate. Authentication will return a token which has a time to live.

You will need to use this token in each subsequent API call to be authorized.

* Step1: [Authenticate](1_0_0#/http/api-endpoints/authentication/get-access-token)
* Step2: [Authorization](1_0_0#/http/getting-started/authorizing-your-client)

### Versioning

When we make backwards-incompatible changes to the API, we will release a new version. The current version is v1.

Earthport considers the following changes to be backwards-compatible:

* Adding new API resources.
* Adding new optional request parameters to existing API methods.
* Adding new properties to existing API responses.
* Changing the order of properties in existing API responses.
* Changing the length or format of object IDs or other opaque strings. 
* Adding new event types. 

   Your webhook listener should gracefully handle unfamiliar events types.

### MIME types
All requests and responses are JSON-formatted and UTF-8 encoded.

An Accept header is required for all requests, for example:

> Accept: application/json

A Content-Type header must be given when sending data to the API (using POST and PUT endpoints), for example:

> Content-Type: application/json

For both of these headers, you must give the standard JSON MIME type (application/json).

You will receive an error (HTTP status code=415) if you attempt to make a POST/PUT request without this MIME type.

### Rate limiting

TBD

#### HTTP Headers and Response Codes
Each response has HTTP headers that provide data on where your application is at for a given rate limit.

**X-Rate-Limit-Limit:** the rate limit ceiling for that given request
 
**X-Rate-Limit-Remaining:** the number of requests left for the 1 minute window

**X-Rate-Limit-Reset:** the remaining window before the rate limit resets

When the rate limit is applied the API will return status code HTTP 429 Too Many Requests. In which case you should wait 60 seconds before retrying.