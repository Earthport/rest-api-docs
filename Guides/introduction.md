The Earthport API is organised around [REST](https://en.wikipedia.org/wiki/Representational_state_transfer). Our API has predictable, resource-oriented URLs, and uses HTTP response codes to indicate API errors. 

We use built-in HTTP features, like HTTP authentication and HTTP verbs, which are understood by off-the-shelf HTTP clients. We support [cross-origin resource sharing](https://en.wikipedia.org/wiki/Cross-origin_resource_sharing), allowing you to interact securely with our API from a client-side web applications.

You should never expose your secret API key in any public website's client-side code. 

JSON is returned by all API responses, including errors, although our API libraries convert responses to appropriate language-specific objects.

### Developer testing steps

We recommend that you:-

1. Read our API documentation first (see [Payment Flows](1_0_0#/http/guides/payment-flows))
2. Download and use our [Postman collection](https://github.com/Earthport/rest-api-postman) to understand our data types and use cases (these contain sample requests)
3. Download the appropriate language SDK and call our APIs from your local developer machine
4. You can test our webhooks using the simulator
5. Once you've carried out the above then you're ready to integrate our APIs into your system(s).

### How to download SDKs

At the top left hand corner of this documentation, is a list box of supported languages:

![alt text](https://raw.githubusercontent.com/Earthport/rest-api-docs/master/images/list_languages.png "List of programming languages")

Choose your programming language from the list, e.g. Java.

This will then load up Java specific help pages within the documentation. You will see various menu options on the left: 

![alt text](https://raw.githubusercontent.com/Earthport/rest-api-docs/master/images/selected_language_java.png "List of Java related documentation")

If you look at the top right hand corner of the screen, you will see a download button where you can download the SDK in this case a Java SDK. 

![alt text](https://raw.githubusercontent.com/Earthport/rest-api-docs/master/images/download_sdk.png "Download SDK")