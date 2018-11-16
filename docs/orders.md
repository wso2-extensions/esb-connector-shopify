# Working with Orders

[[Overview]](#overview)  [[Operation details]](#operation-details)  [[Sample configuration]](#sample-configuration)

### Overview 

The following operations allow you to work with orders. Click an operation name to see details on how to use it.
For a sample proxy service that illustrates how to work with orders, see [Sample configuration](#sample-configuration).

| Operation        | Description |
| ------------- |-------------|
| [createOrder](#creating-an-order)    | Creates a new order. |
| [listOrders](#retrieving-orders)      | Retrieves a list of order. |

### Operation details

This section provides more details on each of the operations related to orders.

#### Creating an order

The createOrder operation creates a new order.

**createOrder**
```xml
<shopify.createOrder>
    <order>{$ctx:order}</order>
</shopify.createOrder>
```
**Properties**
* order: The order details required to create an order.

**Sample request**

Following is a sample request that can be handled by the createOrder operation.

```json
{
    "apiUrl": "https://wso2test-2.myshopify.com",
    "accessToken": "97c7c760cdb6a8ed800c7fdcb3337dce",
    "format": "json",
    "order": {
    "line_items": [
        {
            "variant_id": 943188183,
            "quantity": 1
        }
    ],
    "customer": {
        "first_name": "Paul",
        "last_name": "Norman",
        "email": "paul.norman@example.com"
    },
    "billing_address": {
        "first_name": "John",
        "last_name": "Smith",
        "address1": "123 Fake Street",
        "phone": "555-555-5555",
        "city": "Fakecity",
        "province": "Ontario",
        "country": "Canada",
        "zip": "H0H0H0"
    },
    "shipping_address": {
        "first_name": "Jane",
        "last_name": "Smith",
        "address1": "123 Fake Street",
        "phone": "777-777-7777",
        "city": "Fakecity",
        "province": "Ontario",
        "country": "Canada",
        "zip": "H0H0H0"
    },
    "email": "jane@example.com",
    "transactions": [
        {
            "kind": "authorization",
            "status": "success",
            "amount": 50
        }
    ],
    "financial_status": "partially_paid"
    }
}
```
**Sample response**

Given below is a sample response for the createOrder operation.

```json
{
   "order":{
      "id":1073459966,
      "email":"",
      "closed_at":null,
      "created_at":"2018-11-02T12:35:56-04:00",
      "updated_at":"2018-11-02T12:35:56-04:00",
      "number":2,
      "note":null,
      "token":"a3ec8aec048bc7e326f142182b3221c7",
      "gateway":"",
      "test":false,
      "total_price":"199.00",
      "subtotal_price":"199.00",
      "total_weight":0,
      "total_tax":"0.00",
      "taxes_included":false,
      "currency":"USD",
      "financial_status":"paid",
      "confirmed":true,
      "total_discounts":"0.00",
      "total_line_items_price":"199.00",
      "cart_token":null,
      "buyer_accepts_marketing":false,
      "name":"#1002",
      "total_price_usd":"199.00",
      "processed_at":"2018-11-02T12:35:56-04:00",
      "device_id":null,
      "phone":null,
      "customer_locale":null,
      "app_id":755357713,
      "browser_ip":null,
      "landing_site_ref":null,
      "order_number":1002,
      "discount_applications":[

      ],
      "discount_codes":[

      ],
      "note_attributes":[

      ],
      "payment_gateway_names":[

      ],
      .
      .
   }
}
```

**Related Shopify documentation**

[https://help.shopify.com/en/api/reference/orders/order#create](https://help.shopify.com/en/api/reference/orders/order#create)

#### Retrieving orders

The listOrders operation retrieves a list of orders according to the given filters.

**listOrders**
```xml
<shopify.listOrders>
    <updatedAfter>{$ctx:updatedAfter}</updatedAfter>
    <limit>{$ctx:limit}</limit>
    <updatedBefore>{$ctx:updatedBefore}</updatedBefore>
    <sinceId>{$ctx:sinceId}</sinceId>
    <createdAfter>{$ctx:createdAfter}</createdAfter>
    <status>{$ctx:status}</status>
    <page>{$ctx:page}</page>
    <financialStatus>{$ctx:financialStatus}</financialStatus>
    <fulfillmentStatus>{$ctx:fulfillmentStatus}</fulfillmentStatus>
    <importedBefore>{$ctx:importedBefore}</importedBefore>
    <createdBefore>{$ctx:createdBefore}</createdBefore>
    <importedAfter>{$ctx:importedAfter}</importedAfter>
    <fields>{$ctx:fields}</fields>
</shopify.listOrders>
```
**Properties**
* createdAfter: Shows the orders created after the specified date (format: 2008-12-31 03:00).
* createdBefore: Shows the orders created before the specified date (format: 2008-12-31 03:00).
* updatedAfter: Shows the orders last updated after the specified date (format: 2008-12-31 03:00).
* updatedBefore: Shows the orders last updated before the specified date (format: 2008-12-31 03:00).
* limit: The limit specifies the number of results; defaults to "50".
* page: The page specifies the page to show; defaults to "1".
* fields: The comma-separated list of fields which specifies the response fields.
* sinceId: A order identifier. The response will only list the orders having identifiers higher than this.
* importedAfter: Shows the orders last imported after the specified date (format: 2008-12-31 03:00).
* importedBefore: Shows the orders last imported before the specified date (format: 2008-12-31 03:00).
* status: The status of the order.
* financialStatus: The financial status of the order.
* fulfillmentStatus: The fulfillment status of the order.



**Sample request**

Following is a sample request that can be handled by the listOrders operation.

```json
{
    "accessToken":"97c7c760cdb6a8ed800c7fdcb3337dce",
    "apiUrl":"https://wso2test-2.myshopify.com",
    "format":"json",
    "updatedAfter":"",
    "limit":"",
    "updatedBefore":"",
    "sinceId":"",
    "createdAfter":"",
    "status":"",
    "page":"",
    "financialStatus":"",
    "fulfillmentStatus":"",
    "importedBefore":"",
    "createdBefore":"",
    "importedAfter":"",
    "fields":""
}
```
**Sample response**

Given below is a sample response for the listOrders operation.

```json
{
   "orders":[
      {
         "id":450789469,
         "email":"bob.norman@hostmail.com",
         "closed_at":null,
         "created_at":"2008-01-10T11:00:00-05:00",
         "updated_at":"2008-01-10T11:00:00-05:00",
         "number":1,
         "note":null,
         "token":"b1946ac92492d2347c6235b4d2611184",
         "gateway":"authorize_net",
         "test":false,
         "total_price":"409.94",
         "subtotal_price":"398.00",
         "total_weight":0,
         "total_tax":"11.94",
         "taxes_included":false,
         "currency":"USD",
         "financial_status":"authorized",
         "confirmed":false,
         "total_discounts":"0.00",
         "total_line_items_price":"398.00",
         "cart_token":"68778783ad298f1c80c3bafcddeea02f",
         "buyer_accepts_marketing":false,
         "name":"#1001",
         "referring_site":"http://www.otherexample.com",
         "landing_site":"http://www.example.com?source=abc",
         "cancelled_at":null,
         "cancel_reason":null,
         "total_price_usd":"409.94",
         "checkout_token":"bd5a8aa1ecd019dd3520ff791ee3a24c",
         "reference":"fhwdgads",
         "user_id":null,
         "location_id":null,
         "source_identifier":"fhwdgads",
         "source_url":null,
         "processed_at":"2008-01-10T11:00:00-05:00",
         "device_id":null,
         "phone":"+557734881234",
         "customer_locale":null,
         "app_id":null,
         "browser_ip":null,
         "landing_site_ref":null,
         "order_number":1001,
         "discount_applications":[
         ],
         .
         .
      }
   ]
}
```

**Related Shopify documentation**

[https://help.shopify.com/en/api/reference/orders/order#index](https://help.shopify.com/en/api/reference/orders/order#index)

### Sample configuration

Following example illustrates how to connect to Shopify with the init operation and createOrder operation.

1. Create a sample proxy as below :

```xml
<?xml version="1.0" encoding="UTF-8"?>
<proxy xmlns="http://ws.apache.org/ns/synapse"
       name="createOrder"
       transports="https,http"
       statistics="disable"
       trace="disable"
       startOnLoad="true">
        
        <target>
            <inSequence onError="faultHandlerSeq">
                <property name="apiUrl" expression="json-eval($.apiUrl)" />
                <property name="accessToken" expression="json-eval($.accessToken)" />
                <property name="format" expression="json-eval($.format)" />
                <property name="order" expression="json-eval($.order)" />
                <shopify.init>
                    <apiUrl>{$ctx:apiUrl}</apiUrl>
                    <accessToken>{$ctx:accessToken}</accessToken>
                    <format>{$ctx:format}</format>
                </shopify.init>
                <shopify.createOrder>
                    <order>{$ctx:order}</order>
                </shopify.createOrder>
                <respond />
            </inSequence>
            <outSequence>
                <send />
            </outSequence>
        </target>
        <description />
</proxy>
```

2. Create a json file named createOrder.json and copy the configurations given below to it:

```json
{
    "apiUrl" : "https://wso2test-2.myshopify.com",
    "accessToken" : "97c7c760cdb6a8ed800c7fdcb3337dce",
    "format" : "json",
    "orderId" : "277118679",
    "limit" : "",
    "page" : "",
    "sinceId" : "",
    "createdAfter" : "",
    "createdBefore" : "",
    "updatedAfter" : "",
    "updatedBefore" : "",
    "fields" : ""
}
```
3. Replace the credentials with your values.

4. Execute the following curl command:

```bash
curl http://localhost:8280/services/createOrder -H "Content-Type: application/json" -d @createOrder.json
```

5. Shopify returns a json response similar to the one shown below:
 
```json
{
   "order":{
      "id":1073459966,
      "email":"",
      "closed_at":null,
      "created_at":"2018-11-02T12:35:56-04:00",
      "updated_at":"2018-11-02T12:35:56-04:00",
      "number":2,
      "note":null,
      "token":"a3ec8aec048bc7e326f142182b3221c7",
      "gateway":"",
      "test":false,
      "total_price":"199.00",
      "subtotal_price":"199.00",
      "total_weight":0,
      "total_tax":"0.00",
      "taxes_included":false,
      "currency":"USD",
      "financial_status":"paid",
      "confirmed":true,
      "total_discounts":"0.00",
      "total_line_items_price":"199.00",
      "cart_token":null,
      "buyer_accepts_marketing":false,
      "name":"#1002",
      "total_price_usd":"199.00",
      "processed_at":"2018-11-02T12:35:56-04:00",
      "device_id":null,
      "phone":null,
      "customer_locale":null,
      "app_id":755357713,
      "browser_ip":null,
      "landing_site_ref":null,
      "order_number":1002,
      "discount_applications":[

      ],
      "discount_codes":[

      ],
      "note_attributes":[

      ],
      "payment_gateway_names":[

      ],
      .
      .
   }
}
```
