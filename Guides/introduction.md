## Introduction
The Earthport API is organised around [REST](https://en.wikipedia.org/wiki/Representational_state_transfer). Our API has predictable, resource-oriented URLs, and uses HTTP response codes to indicate API errors. 

We use built-in HTTP features, like HTTP authentication and HTTP verbs, which are understood by off-the-shelf HTTP clients. We support [cross-origin resource sharing](https://en.wikipedia.org/wiki/Cross-origin_resource_sharing), allowing you to interact securely with our API from a client-side web applications.

You should never expose your secret API key in any public website's client-side code. 

JSON is returned by all API responses, including errors, although our API libraries convert responses to appropriate language-specific objects.

### Developer testing steps

We recommend that you:-

1. Read our API documentation first
2. Download and use our [Postman collection](https://github.com/Earthport/rest-api-postman) to understand our data types and uses cases (these contain sample requests)
3. Download the appropriate language SDK and call our APIs from your local developer machine
4. You can test our webhooks using the simulator
5. Once you've carried out the above then you're ready to integrate our APIs into your system(s).