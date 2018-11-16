# Working with Fulfillments

[[Overview]](#overview)  [[Operation details]](#operation-details)  [[Sample configuration]](#sample-configuration)

### Overview 

The following operations allow you to work with fulfillments. Click an operation name to see details on how to use it.
For a sample proxy service that illustrates how to work with fulfillments, see [Sample configuration](#sample-configuration).

| Operation        | Description |
| ------------- |-------------|
| [createFulfillment](#creating-a-fulfillment)    | Creates a fulfillment. |
| [listFulfillments](#retrieving-fulfillments)      | Retrieves a list of fulfillments. |

### Operation details

This section provides more details on each of the operations related to fulfillments.

#### Creating a fulfillment

The createFulfillment operation creates a fulfillment for the specified order and line items.

**createFulfillment**
```xml
<shopify.createFulfillment>
    <fulfillment>{$ctx:fulfillment}</fulfillment>
    <orderId>{$ctx:orderId}</orderId>
</shopify.createFulfillment>
```
**Properties**
* fulfillment: An object containing the fulfillment details.
* orderId: The unique numeric identifier for an order.

**Sample request**

Following is a sample request that can be handled by the createFulfillment operation.

```json
{
    "accessToken":"97c7c760cdb6a8ed800c7fdcb3337dce",
    "apiUrl":"https://wso2test-2.myshopify.com",
    "format":"json",
    "fulfillment": {
    "tracking_number": "trackNo1",
       "notify_customer": true
     },
    "orderId":"277808615"
}
```
**Sample response**

Given below is a sample response for the createFulfillment operation.

```json
{
   "fulfillment":{
      "id":1022782904,
      "order_id":450789469,
      "status":"success",
      "created_at":"2018-10-03T14:47:33-04:00",
      "service":"manual",
      "updated_at":"2018-10-03T14:47:33-04:00",
      "tracking_company":"Bluedart",
      "shipment_status":null,
      "location_id":905684977,
      "tracking_number":"123456789",
      "tracking_numbers":[
         "123456789"
      ],
      "tracking_url":"https://shipping.xyz/track.php?num=123456789",
      "tracking_urls":[
         "https://shipping.xyz/track.php?num=123456789",
         "https://anothershipper.corp/track.php?code=abc"
      ],
      "receipt":{

      },
      "name":"#1001.1",
      "admin_graphql_api_id":"gid://shopify/Fulfillment/1022782904",
      "line_items":[
         {
            "id":466157049,
            "variant_id":39072856,
            "title":"IPod Nano - 8gb",
            "quantity":1,
            "price":"199.00",
            "sku":"IPOD2008GREEN",
            "variant_title":"green",
            "vendor":null,
            "fulfillment_service":"manual",
            "product_id":632910392,
            "requires_shipping":true,
            "taxable":true,
            "gift_card":false,
            "name":"IPod Nano - 8gb - green",
            "variant_inventory_management":"shopify",
            "properties":[
               {
                  "name":"Custom Engraving Front",
                  "value":"Happy Birthday"
               },
               {
                  "name":"Custom Engraving Back",
                  "value":"Merry Christmas"
               }
            ],
            "product_exists":true,
            "fulfillable_quantity":0,
            "grams":200,
            "total_discount":"0.00",
            "fulfillment_status":"fulfilled",
            "discount_allocations":[

            ],
            "admin_graphql_api_id":"gid://shopify/LineItem/466157049",
            "tax_lines":[
               {
                  "title":"State Tax",
                  "price":"3.98",
                  "rate":0.06
               }
            ]
         },
         .
         .
      ]
   }
}
```

**Related Shopify documentation**

[https://help.shopify.com/en/api/reference/shipping_and_fulfillment/fulfillment#create](https://help.shopify.com/en/api/reference/shipping_and_fulfillment/fulfillment#create)

#### Retrieving fulfillments

The listFulfillments operation retrieves a list of all fulfillments.

**listFulfillments**
```xml
<shopify.listFulfillments>
    <orderId>{$ctx:orderId}</orderId>
    <limit>{$ctx:limit}</limit>
    <page>{$ctx:page}</page>
    <sinceId>{$ctx:sinceId}</sinceId>
    <createdAfter>{$ctx:createdAfter}</createdAfter>
    <createdBefore>{$ctx:createdBefore}</createdBefore>
    <updatedAfter>{$ctx:updatedAfter}</updatedAfter>
    <updatedBefore>{$ctx:updatedBefore}</updatedBefore>
    <fields>{$ctx:fields}</fields>
</shopify.listFulfillments>
```
**Properties**
* orderId: The Order ID.
* createdAfter: Shows the fulfillments created after the specified date (format: 2008-12-31 03:00).
* createdBefore: Shows the fulfillments created before the specified date (format: 2008-12-31 03:00).
* updatedAfter: Shows the fulfillments last updated after the specified date (format: 2008-12-31 03:00).
* updatedBefore: Shows the fulfillments last updated before the specified date (format: 2008-12-31 03:00).
* limit: The limit specifies the number of results; defaults to "50".
* page: The page specifies the page to show; defaults to "1".
* fields: The comma-separated list of fields which specifies the response fields.
* sinceId: A fulfillment identifier. The response will only list the fulfillments having identifiers higher than this.


**Sample request**

Following is a sample request that can be handled by the listFulfillments operation.

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
**Sample response**

Given below is a sample response for the listFulfillments operation.

```json
{
   "fulfillments":[
      {
         "id":255858046,
         "order_id":450789469,
         "status":"failure",
         "created_at":"2018-10-03T14:19:25-04:00",
         "service":"manual",
         "updated_at":"2018-10-03T14:19:25-04:00",
         "tracking_company":null,
         "shipment_status":null,
         "location_id":905684977,
         "tracking_number":"1Z2345",
         "tracking_numbers":[
            "1Z2345"
         ],
         "tracking_url":"http://wwwapps.ups.com/etracking/tracking.cgi?InquiryNumber1=1Z2345&TypeOfInquiryNumber=T&AcceptUPSLicenseAgreement=yes&submit=Track",
         "tracking_urls":[
            "http://wwwapps.ups.com/etracking/tracking.cgi?InquiryNumber1=1Z2345&TypeOfInquiryNumber=T&AcceptUPSLicenseAgreement=yes&submit=Track"
         ],
         "receipt":{
            "testcase":true,
            "authorization":"123456"
         },
         "name":"#1001.0",
         "admin_graphql_api_id":"gid://shopify/Fulfillment/255858046",
         "line_items":[
            {
               "id":466157049,
               "variant_id":39072856,
               "title":"IPod Nano - 8gb",
               "quantity":1,
               "price":"199.00",
               "sku":"IPOD2008GREEN",
               "variant_title":"green",
               "vendor":null,
               "fulfillment_service":"manual",
               "product_id":632910392,
               "requires_shipping":true,
               "taxable":true,
               "gift_card":false,
               "name":"IPod Nano - 8gb - green",
               "variant_inventory_management":"shopify",
               .
               .
            }
         ]
      }
   ]
}
```

**Related Shopify documentation**

[https://help.shopify.com/en/api/reference/shipping_and_fulfillment/fulfillment#index](https://help.shopify.com/en/api/reference/shipping_and_fulfillment/fulfillment#index)

### Sample configuration

Following example illustrates how to connect to Shopify with the init operation and createFulfillment operation.

1. Create a sample proxy as below :

```xml
<?xml version="1.0" encoding="UTF-8"?>
  <proxy xmlns="http://ws.apache.org/ns/synapse" name="createFulfillment" transports="https,http" statistics="disable" trace="disable" startOnLoad="true">
   <target>
   <inSequence>
      <property name="accessToken" expression="json-eval($.accessToken)"/>
      <property name="apiUrl" expression="json-eval($.apiUrl)"/>
      <property name="format" expression="json-eval($.format)"/>
      <property name="fulfillment" expression="json-eval($.fulfillment)"/>
      <property name="orderId" expression="json-eval($.orderId)"/>
      <shopify.init>
         <accessToken>{$ctx:accessToken}</accessToken>
         <apiUrl>{$ctx:apiUrl}</apiUrl>
         <format>{$ctx:format}</format>
      </shopify.init>
      <shopify.createFulfillment>
         <fulfillment>{$ctx:fulfillment}</fulfillment>
         <orderId>{$ctx:orderId}</orderId>
      </shopify.createFulfillment>
     <respond/>
   </inSequence>
    <outSequence>
     <send/>
    </outSequence>
   </target>
   <description/>
  </proxy>
```

2. Create a json file named createFulfillment.json and copy the configurations given below to it:

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
curl http://localhost:8280/services/createFulfillment -H "Content-Type: application/json" -d @createFulfillment.json
```

5. Shopify returns a json response similar to the one shown below:
 
```json
{
   "fulfillment":{
      "id":1022782904,
      "order_id":450789469,
      "status":"success",
      "created_at":"2018-10-03T14:47:33-04:00",
      "service":"manual",
      "updated_at":"2018-10-03T14:47:33-04:00",
      "tracking_company":"Bluedart",
      "shipment_status":null,
      "location_id":905684977,
      "tracking_number":"123456789",
      "tracking_numbers":[
         "123456789"
      ],
      "tracking_url":"https://shipping.xyz/track.php?num=123456789",
      "tracking_urls":[
         "https://shipping.xyz/track.php?num=123456789",
         "https://anothershipper.corp/track.php?code=abc"
      ],
      "receipt":{

      },
      "name":"#1001.1",
      "admin_graphql_api_id":"gid://shopify/Fulfillment/1022782904",
      "line_items":[
         {
            "id":466157049,
            "variant_id":39072856,
            "title":"IPod Nano - 8gb",
            "quantity":1,
            "price":"199.00",
            "sku":"IPOD2008GREEN",
            "variant_title":"green",
            "vendor":null,
            "fulfillment_service":"manual",
            "product_id":632910392,
            "requires_shipping":true,
            "taxable":true,
            "gift_card":false,
            "name":"IPod Nano - 8gb - green",
            "variant_inventory_management":"shopify",
            "properties":[
               {
                  "name":"Custom Engraving Front",
                  "value":"Happy Birthday"
               },
               {
                  "name":"Custom Engraving Back",
                  "value":"Merry Christmas"
               }
            ],
            "product_exists":true,
            "fulfillable_quantity":0,
            "grams":200,
            "total_discount":"0.00",
            "fulfillment_status":"fulfilled",
            "discount_allocations":[

            ],
            "admin_graphql_api_id":"gid://shopify/LineItem/466157049",
            "tax_lines":[
               {
                  "title":"State Tax",
                  "price":"3.98",
                  "rate":0.06
               }
            ]
         },
         .
         .
      ]
   }
}
```
