# Configuring Shopify Operations

[[Prerequisites]](#Prerequisites) [[Initializing the connector]](#initializing-the-connector)

## Prerequisites

To use the Shopify connector, add the  <shopify.init>  element in your configuration before carrying out any other Shopify operations. 

### Obtaining user credentials

Shopify uses an access token which needs to be generated.  For more information on authentication, see http://docs.shopify.com/api/authentication/oauth.

### Importing the Shopify Certificate

Before you start configuring the connector, import the Shopify certificate to your EI client keystore.

* Follow the steps below to import the Shopify certificate into the EI client keystore:

    1. Extract the certificate from browse by navigating to ' https://{shop_name}.myshopify.com ' and click the lock icon on the address bar to view the certificate.
    2. Export the certificate to the file system.
    3. Import the certificate to the EI client keystore using either the following command or the EI Management Console:
    ```
    keytool -importcert -file <certificate file> -keystore <EI>/repository/resources/security/client-truststore.jks -alias "Shopify"
    ```
    4. Restart the server and deploy the Shopify configuration. 
    

## Initializing the connector

Add the following <shopify.init> method in your configuration:
 
#### init
```xml
<shopify.init>
    <accessToken>{$ctx:accessToken}</accessToken>
    <apiUrl>{$ctx:apiUrl}</apiUrl>
    <format>{$ctx:format}</format>
</shopify.init>
```
**Properties** 
* accessToken:  Encrypted alphanumeric strings to authenticate the Shopify credentials.
* apiUrl:  The API URL of Shopify.
* format:  The response type which specifies the return type, e.g. json.

Now that you have connected to Shopify, use the information in the following topics to perform various operations with the connector. Also, see [Configuring the Shopify Connector Fault Handler Sequence](fault_handler_sequence.md).

[Working with Customers](customers.md)

[Working with Fulfillments](fulfillments.md)

[Working with Orders](orders.md)

[Working with Products](products.md)
