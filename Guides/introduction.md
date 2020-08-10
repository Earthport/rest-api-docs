We at Visa Payments Limited provide all our clients with our [REST](https://en.wikipedia.org/wiki/Representational_state_transfer)ful API service - it's easy to use, has predictable resource-oriented URLs, and demonstrates the use of HTTP response codes in order to indicate any API errors that may occur. 

We use built-in HTTP features such as HTTP authentication and HTTP verbs, which are understood by off-the-shelf HTTP clients. Furthermore, we support [cross-origin resource sharing](https://en.wikipedia.org/wiki/Cross-origin_resource_sharing), allowing you to interact securely with our API from client-side web applications. However we strongly advise that you _NEVER_ expose your secret API key in any public website's client-side code. 

The default file format returned by every API response is JSON - including errors, although our API libraries convert responses to appropriate language-specific objects.

### Developer testing steps

We recommend that you:

1. Start by reading our API documentation first (see [Payment Flows](#/http/guides/payment-flows))
2. Download and use our [Postman collection](https://github.com/Earthport/rest-api-postman) to understand our data types and use cases (these contain sample requests)
3. Download the appropriate language SDK and call our APIs from your local developer machine
4. You can test our webhooks using the simulator
5. Once you've carried out the above then you're ready to integrate our APIs into your system(s).

### How to download SDKs

At the top left hand corner of this documentation is a list box of supported languages:

![alt text](https://raw.githubusercontent.com/Earthport/rest-api-docs/master/images/list_languages.png "List of programming languages")

Choose your programming language from the list, e.g. Java.

This will then load up Java specific help pages within the documentation. You will see various menu options on the left: 

![alt text](https://raw.githubusercontent.com/Earthport/rest-api-docs/master/images/selected_language_java.png "List of Java related documentation")

If you look at the left hand side of the screen underneath the selected programming language, you will see a 'Get SDK' button in Yellow where you can download the SDK in this case a Java SDK. 

![alt text](https://raw.githubusercontent.com/Earthport/rest-api-docs/master/images/get_sdk.PNG "Get SDK")