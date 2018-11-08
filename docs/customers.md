# Working with Customers

[[Overview]](#overview)  [[Operation details]](#operation-details)  [[Sample configuration]](#sample-configuration)

### Overview 

The following operations allow you to work with customers. Click an operation name to see details on how to use it.
For a sample proxy service that illustrates how to work with customers, see [Sample configuration](#sample-configuration).

| Operation        | Description |
| ------------- |-------------|
| [createCustomer](#creating-a-customer)    | Creates a new customer. |
| [listCustomers](#retrieving-customers)      | Retrieves all customers of a shop. |

### Operation details

This section provides more details on each of the operations related to customers.

#### Creating a customer

The createCustomer operation creates a new customer record.

**createCustomer**
```xml
<shopify.createCustomer>
    <customer>{$ctx:customer}</customer>
</shopify.createCustomer>
```
**Properties**
* customer: The customer object containing the data to create the customer.

**Sample request**

Following is a sample request that can be handled by the createCustomer operation.

```json
{
   "apiUrl":"https://wso2test-2.myshopify.com",
   "accessToken":"97c7c760cdb6a8ed800c7fdcb3337dce",
   "format":"json",
   "customer":{
      "first_name":"FirstName",
      "last_name":"LastName",
      "email":"test2.test@test.com",
      "verified_email":true,
      "addresses":[
         {
            "address1":"Address1",
            "city":"City",
            "province":"ON",
            "phone":"555-1212",
            "zip":"123 ABC",
            "last_name":"Lastnameson",
            "first_name":"Mother",
            "country":"CA"
         }
      ]
   }
}
```
**Sample response**

Given below is a sample response for the createCustomer operation.

```json
{
   "customer":{
      "id":1073339466,
      "email":"steve.lastnameson@example.com",
      "accepts_marketing":false,
      "created_at":"2018-10-23T15:42:21-04:00",
      "updated_at":"2018-10-23T15:42:21-04:00",
      "first_name":"Steve",
      "last_name":"Lastnameson",
      "orders_count":0,
      "state":"disabled",
      "total_spent":"0.00",
      "last_order_id":null,
      "note":null,
      "verified_email":true,
      "multipass_identifier":null,
      "tax_exempt":false,
      "phone":"+15142546011",
      "tags":"",
      "last_order_name":null,
      "currency":"USD",
      "addresses":[] 
   }
}
```

**Related Shopify documentation**

[https://help.shopify.com/en/api/reference/customers/customer#create](https://help.shopify.com/en/api/reference/customers/customer#create)

#### Retrieving customers

The listCustomers operation retrieves all customers in a shop.

**listCustomers**
```xml
<shopify.listCustomers>
    <sinceId>{$ctx:sinceId}</sinceId>
    <createdAfter>{$ctx:createdAfter}</createdAfter>
    <createdBefore>{$ctx:createdBefore}</createdBefore>
    <updatedAfter>{$ctx:updatedAfter}</updatedAfter>
    <updatedBefore>{$ctx:updatedBefore}</updatedBefore>
    <limit>{$ctx:limit}</limit>
    <page>{$ctx:page}</page>
    <fields>{$ctx:fields}</fields>
</shopify.listCustomers>
```
**Properties**
* sinceId: A customer identifier. The response will only list customers having identifiers higher than this.
* createdAfter: Shows customers created after the specified date (format: 2008-12-31 03:00).
* createdBefore: Shows customers created before the specified date (format: 2008-12-31 03:00).
* updatedAfter: Shows customers last updated after the specified date (format: 2008-12-31 03:00).
* updatedBefore: Shows customers last updated before the specified date (format: 2008-12-31 03:00).
* limit: The limit specifies the number of results; defaults to "50".
* page: The page specifies the page to show; defaults to "1".
* fields: The comma-separated list of fields which specifies the response fields.


**Sample request**

Following is a sample request that can be handled by the listCustomers operation.

```json
{
    "apiUrl" : "https://wso2test-2.myshopify.com",
    "accessToken" : "97c7c760cdb6a8ed800c7fdcb3337dce",
    "format" : "json",
    "sinceId" : "",
    "createdAfter" : "",
    "createdBefore" : "",
    "updatedAfter" : "",
    "updatedBefore" : "",
    "limit" : "",
    "page" : "",
    "fields" : ""
}
```
**Sample response**

Given below is a sample response for the listCustomers operation.

```json
{
   "customers":[
      {
         "id":207119551,
         "email":"bob.norman@hostmail.com",
         "accepts_marketing":false,
         "created_at":"2018-10-23T15:29:24-04:00",
         "updated_at":"2018-10-23T15:29:24-04:00",
         "first_name":"Bob",
         "last_name":"Norman",
         "orders_count":1,
         "state":"disabled",
         "total_spent":"41.94",
         "last_order_id":450789469,
         "note":null,
         "verified_email":true,
         "multipass_identifier":null,
         "tax_exempt":false,
         "phone":null,
         "tags":"",
         "last_order_name":"#1001",
         "currency":"USD",
         "addresses":[
            {
               "id":207119551,
               "customer_id":207119551,
               "first_name":null,
               "last_name":null,
               "company":null,
               "address1":"Chestnut Street 92",
               "address2":"",
               "city":"Louisville",
               "province":"Kentucky",
               "country":"United States",
               "zip":"40202",
               "phone":"555-625-1199",
               "name":"",
               "province_code":"KY",
               "country_code":"US",
               "country_name":"United States",
               "default":true
            }
         ]
      },
      .
      .
   ]
}
```

**Related Shopify documentation**

[https://help.shopify.com/en/api/reference/customers/customer#index](https://help.shopify.com/en/api/reference/customers/customer#index)

### Sample configuration

Following example illustrates how to connect to Shopify with the init operation and createCustomer operation.

1. Create a sample proxy as below :

```xml
<?xml version="1.0" encoding="UTF-8"?>
<proxy xmlns="http://ws.apache.org/ns/synapse" name="createCustomer" transports="https,http" statistics="disable"
    trace="disable" startOnLoad="true">
    <target>
        <inSequence>
            <property name="apiUrl" expression="json-eval($.apiUrl)" />
            <property name="accessToken" expression="json-eval($.accessToken)" />
            <property name="format" expression="json-eval($.format)" />
            <property name="customer" expression="json-eval($.customer)" />
            <shopify.init>
                <apiUrl>{$ctx:apiUrl}</apiUrl>
                <accessToken>{$ctx:accessToken}</accessToken>
                <format>{$ctx:format}</format>
            </shopify.init>
            <shopify.createCustomer>
                <customer>{$ctx:customer}</customer>
            </shopify.createCustomer>
            <respond />
        </inSequence>
        <outSequence>
            <send />
        </outSequence>
    </target>
    <description />
</proxy>
```

2. Create a json file named createCustomer.json and copy the configurations given below to it:

```json
{
   "apiUrl":"https://wso2test-2.myshopify.com",
   "accessToken":"97c7c760cdb6a8ed800c7fdcb3337dce",
   "format":"json",
   "customer":{
      "first_name":"FirstName",
      "last_name":"LastName",
      "email":"test2.test@test.com",
      "verified_email":true,
      "addresses":[
         {
            "address1":"Address1",
            "city":"City",
            "province":"ON",
            "phone":"555-1212",
            "zip":"123 ABC",
            "last_name":"Lastnameson",
            "first_name":"Mother",
            "country":"CA"
         }
      ]
   }
}
```
3. Replace the credentials with your values.

4. Execute the following curl command:

```bash
curl http://localhost:8280/services/createCustomer -H "Content-Type: application/json" -d @createCustomer.json
```

5. Shopify returns a json response similar to the one shown below:
 
```json
{
   "customer":{
      "id":1073339466,
      "email":"steve.lastnameson@example.com",
      "accepts_marketing":false,
      "created_at":"2018-10-23T15:42:21-04:00",
      "updated_at":"2018-10-23T15:42:21-04:00",
      "first_name":"Steve",
      "last_name":"Lastnameson",
      "orders_count":0,
      "state":"disabled",
      "total_spent":"0.00",
      "last_order_id":null,
      "note":null,
      "verified_email":true,
      "multipass_identifier":null,
      "tax_exempt":false,
      "phone":"+15142546011",
      "tags":"",
      "last_order_name":null,
      "currency":"USD",
      "addresses":[] 
   }
}
```
