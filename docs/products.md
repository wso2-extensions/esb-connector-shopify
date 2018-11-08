# Working with Products

[[Overview]](#overview)  [[Operation details]](#operation-details)  [[Sample configuration]](#sample-configuration)

### Overview 

The following operations allow you to work with products. Click an operation name to see details on how to use it.
For a sample proxy service that illustrates how to work with products, see [Sample configuration](#sample-configuration).

| Operation        | Description |
| ------------- |-------------|
| [createProduct](#creating-a-product)    | Creates a new product. |
| [createProductVariant ](#creating-a-product-variant)      | Creates a new product variant. |
| [getProductById](#retrieving-a-product)    | Retrieves a single product. |
| [listProducts](#retrieving-a-list-of-products)      | Retrieves a list of products. |
| [listProductVariants](#retrieving-a-list-of-product-variants)    | Retrieves  a list of product variants. |

### Operation details

This section provides more details on each of the operations related to products.

#### Creating a product

The createProduct operation creates a new product.

**createProduct**
```xml
<shopify.createProduct>
    <product>{$ctx:product}</product>
</shopify.createProduct>
```
**Properties**
* product: All the product details required to create a new product.

**Sample request**

Following is a sample request that can be handled by the createProduct operation.

```json
{
    "accessToken":"97c7c760cdb6a8ed800c7fdcb3337dce",
    "apiUrl":"https://wso2test-2.myshopify.com",
    "format":"json",
    "product": {
        "title": "Burton Custom Freestyle 151",
        "body_html": "<strong>Good snowboard!</strong>",
        "vendor": "Burton",
        "product_type": "Snowboard",
        "description": "Experience the mystery!",
        "tags": "Barnes & Noble, John's Fav, \"Big Air\"",
        "published": true,
        "variants": [
              {
                "option1": "First",
                "price": "10.00",
                "sku": 123
              },
              {
                "option1": "Second",
                "price": "20.00",
                "sku": "123"
              }
        ],
        "images": [
            {
                    "attachment": "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"
            }
            ],
            "metafields": [
            {
                 "key": "new",
                 "value": "newvalue",
                 "value_type": "string",
                 "namespace": "global"
                }
            ]
    }
}
```
**Sample response**

Given below is a sample response for the createProduct operation.

```json
{
  "product": {
    "id": 1071559620,
    "title": "Burton Custom Freestyle 151",
    "body_html": "<strong>Good snowboard!</strong>",
    "vendor": "Burton",
    "product_type": "Snowboard",
    "created_at": "2018-10-31T13:11:20-04:00",
    "handle": "burton-custom-freestyle-151",
    "updated_at": "2018-10-31T13:11:20-04:00",
    "published_at": "2018-10-31T13:11:20-04:00",
    "template_suffix": null,
    "tags": "&quot;Big Air&quot;, Barnes & Noble, John's Fav",
    "published_scope": "web",
    "admin_graphql_api_id": "gid://shopify/Product/1071559620",
    "variants": [
      {
        "id": 1070325073,
        "product_id": 1071559620,
        "title": "Default Title",
        "price": "0.00",
        "sku": "",
        "position": 1,
        "inventory_policy": "deny",
        "compare_at_price": null,
        "fulfillment_service": "manual",
        "inventory_management": null,
        "option1": "Default Title",
        "option2": null,
        "option3": null,
        "created_at": "2018-10-31T13:11:20-04:00",
        "updated_at": "2018-10-31T13:11:20-04:00",
        "taxable": true,
        "barcode": null,
        "grams": 0,
        "image_id": null,
        "weight": 0.0,
        "weight_unit": "lb",
        "inventory_item_id": 1070325081,
        "inventory_quantity": 0,
        "old_inventory_quantity": 0,
        "requires_shipping": true,
        "admin_graphql_api_id": "gid://shopify/ProductVariant/1070325073",
        "presentment_prices": [
          {
            "price": {
              "currency_code": "USD",
              "amount": "0.00"
            },
            "compare_at_price": null
          }
        ]
      }
    ],
    "options": [
      {
        "id": 1022828690,
        "product_id": 1071559620,
        "name": "Title",
        "position": 1,
        "values": [
          "Default Title"
        ]
      }
    ],
    "images": [],
    "image": null
  }
}
```

**Related Shopify documentation**

[https://help.shopify.com/en/api/reference/products/product#create](https://help.shopify.com/en/api/reference/products/product#create)

#### Creating a product variant 

The createProductVariant operation creates a new product variant.

**createProductVariant**
```xml
<shopify.createProductVariant>
    <productId>{$ctx:productId}</productId>
    <variant>{$ctx:variant}</variant>
</shopify.createProductVariant>
```
**Properties**
* productId: The product ID is used to identify a specific product.
* variant: The variant is a different version of a product, such as differing sizes or differing colors.

**Sample request**

Following is a sample request that can be handled by the createProductVariant operation.

```json
{
    "apiUrl": "https://wso2test-2.myshopify.com",
    "accessToken": "97c7c760cdb6a8ed800c7fdcb3337dce",
    "format": "json",
    "productId":"402818019",
    "variant": {
            "option1": "Test3",
            "price": "1.00",
            "image_id": 929449691,
            "metafields": [
              {
                "key": "new",
                "value": "newvalue",
                "value_type": "string",
                "namespace": "global"
              }
            ]
    }
}
```
**Sample response**

Given below is a sample response for the createProductVariant operation.

```json
{
  "product": {
    "id": 1071559622,
    "title": "Burton Custom Freestyle 151",
    "body_html": "<strong>Good snowboard!</strong>",
    "vendor": "Burton",
    "product_type": "Snowboard",
    "created_at": "2018-10-31T13:11:23-04:00",
    "handle": "burton-custom-freestyle-151",
    "updated_at": "2018-10-31T13:11:24-04:00",
    "published_at": "2018-10-31T13:11:23-04:00",
    "template_suffix": null,
    "tags": "",
    "published_scope": "web",
    "admin_graphql_api_id": "gid://shopify/Product/1071559622",
    "variants": [
      {
        "id": 1070325075,
        "product_id": 1071559622,
        "title": "First",
        "price": "10.00",
        "sku": "123",
        "position": 1,
        "inventory_policy": "deny",
        "compare_at_price": null,
        "fulfillment_service": "manual",
        "inventory_management": null,
        "option1": "First",
        "option2": null,
        "option3": null,
        "created_at": "2018-10-31T13:11:23-04:00",
        "updated_at": "2018-10-31T13:11:23-04:00",
        "taxable": true,
        "barcode": null,
        "grams": 0,
        "image_id": null,
        "weight": 0.0,
        "weight_unit": "lb",
        "inventory_item_id": 1070325083,
        "inventory_quantity": 0,
        "old_inventory_quantity": 0,
        "requires_shipping": true,
        "admin_graphql_api_id": "gid://shopify/ProductVariant/1070325075",
        "presentment_prices": [
          {
            "price": {
              "currency_code": "USD",
              "amount": "10.00"
            },
            "compare_at_price": null
          }
        ]
      }
    ],
    "options": [
      {
        "id": 1022828692,
        "product_id": 1071559622,
        "name": "Title",
        "position": 1,
        "values": [
          "First",
          "Second"
        ]
      }
    ],
    "images": [],
    "image": null
  }
}
```

**Related Shopify documentation**

[https://help.shopify.com/en/api/reference/products/product_variant#create](https://help.shopify.com/en/api/reference/products/product_variant#create)

#### Retrieving a product

The getProductById operation retrieves a single product.

**getProductById**
```xml
<shopify.getProductById>
    <productId>{$ctx:productId}</productId>
    <fields>{$ctx:fields}</fields>
</shopify.getProductById>
```
**Properties**
* productid: The product ID is used to retrieve details of a specific product.
* fields: The comma-separated list of fields to include in the response.

**Sample request**

Following is a sample request that can be handled by the getProductById operation.

```json
{
    "apiUrl":"https://wso2test-2.myshopify.com",
    "accessToken":"97c7c760cdb6a8ed800c7fdcb3337dce",
    "format":"json",
    "productId":"399673771",
    "fields":"id,handle"
}
```
**Sample response**

Given below is a sample response for the getProductById operation.

```json
{
   "product":{
      "id":632910392,
      "title":"IPod Nano - 8GB",
      "body_html":"<p>It's the small iPod with one very big idea: Video. Now the world's most popular music player, available in 4GB and 8GB models, lets you enjoy TV shows, movies, video podcasts, and more. The larger, brighter display means amazing picture quality. In six eye-catching colors, iPod nano is stunning all around. And with models starting at just $149, little speaks volumes.</p>",
      "vendor":"Apple",
      "product_type":"Cult Products",
      "created_at":"2018-10-31T13:02:19-04:00",
      "handle":"ipod-nano",
      "updated_at":"2018-10-31T13:02:19-04:00",
      "published_at":"2007-12-31T19:00:00-05:00",
      "template_suffix":null,
      "tags":"Emotive, Flash Memory, MP3, Music",
      "published_scope":"web",
      "admin_graphql_api_id":"gid://shopify/Product/632910392",
      "variants":[
         {
            "id":808950810,
            "product_id":632910392,
            "title":"Pink",
            "price":"199.00",
            "sku":"IPOD2008PINK",
            "position":1,
            "inventory_policy":"continue",
            "compare_at_price":null,
            "fulfillment_service":"manual",
            "inventory_management":"shopify",
            "option1":"Pink",
            "option2":null,
            "option3":null,
            "created_at":"2018-10-31T13:02:19-04:00",
            "updated_at":"2018-10-31T13:02:19-04:00",
            "taxable":true,
            "barcode":"1234_pink",
            "grams":567,
            "image_id":562641783,
            "weight":1.25,
            "weight_unit":"lb",
            "inventory_item_id":808950810,
            "inventory_quantity":10,
            "old_inventory_quantity":10,
            "requires_shipping":true,
            "admin_graphql_api_id":"gid://shopify/ProductVariant/808950810",
            "presentment_prices":[
               {
                  "price":{
                     "currency_code":"USD",
                     "amount":"199.00"
                  },
                  "compare_at_price":null
               }
            ]
         }
      ],
      "options":[
         {
            "id":594680422,
            "product_id":632910392,
            "name":"Color",
            "position":1,
            "values":[
               "Pink",
               "Red",
               "Green",
               "Black"
            ]
         }
      ],
      "images":[
         {
            "id":850703190,
            "product_id":632910392,
            "position":1,
            "created_at":"2018-10-31T13:02:19-04:00",
            "updated_at":"2018-10-31T13:02:19-04:00",
            "alt":null,
            "width":123,
            "height":456,
            "src":"https://cdn.shopify.com/s/files/1/0006/9093/3842/products/ipod-nano.png?v=1541005339",
            "variant_ids":[

            ],
            "admin_graphql_api_id":"gid://shopify/ProductImage/850703190"
         }
      ],
      "image":{
         "id":850703190,
         "product_id":632910392,
         "position":1,
         "created_at":"2018-10-31T13:02:19-04:00",
         "updated_at":"2018-10-31T13:02:19-04:00",
         "alt":null,
         "width":123,
         "height":456,
         "src":"https://cdn.shopify.com/s/files/1/0006/9093/3842/products/ipod-nano.png?v=1541005339",
         "variant_ids":[

         ],
         "admin_graphql_api_id":"gid://shopify/ProductImage/850703190"
      }
   }
}
```

**Related Shopify documentation**

[https://help.shopify.com/en/api/reference/products/product#show](https://help.shopify.com/en/api/reference/products/product#show)

#### Retrieving a list of products

The listProducts operation retrieves a list of products.

**listOrders**
```xml
<shopify.listProducts>
    <limit>{$ctx:limit}</limit>
    <page>{$ctx:page}</page>
    <sinceId>{$ctx:sinceId}</sinceId>
    <vendor>{$ctx:vendor}</vendor>
    <handle>{$ctx:handle}</handle>
    <productType>{$ctx:productType}</productType>
    <collectionId>{$ctx:collectionId}</collectionId>
    <createdAfter>{$ctx:createdAfter}</createdAfter>
    <createdBefore>{$ctx:createdBefore}</createdBefore>
    <updatedAfter>{$ctx:updatedAfter}</updatedAfter>
    <updatedBefore>{$ctx:updatedBefore}</updatedBefore>
    <publishedAfter>{$ctx:publishedAfter}</publishedAfter>
    <publishedBefore>{$ctx:publishedBefore}</publishedBefore>
    <publishedStatus>{$ctx:publishedStatus}</publishedStatus>
    <fields>{$ctx:fields}</fields>
</shopify.listProducts>
```
**Properties**
* createdAfter: Shows the products created after the specified date (format: 2008-12-31 03:00).
* createdBefore: Shows the products created before the specified date (format: 2008-12-31 03:00).
* updatedAfter: Shows the products last updated after the specified date (format: 2008-12-31 03:00).
* updatedBefore: Shows the products last updated before the specified date (format: 2008-12-31 03:00).
* limit: The limit specifies the number of results; defaults to "50".
* page: The page specifies the page to show; defaults to "1".
* fields: The comma-separated list of fields which specifies the response fields.
* sinceId: A product identifier. The response will only list the products having identifiers higher than this.
* publishedAfter: Shows the products last published after the specified date (format: 2008-12-31 03:00).
* publishedBefore: Shows the products last published before the specified date (format: 2008-12-31 03:00).
* publishedStatus: The status whether to show published or unpublished or all products.
* vendor: Filters by product vendor.
* handle: Filters by product handle.
* productType: Filters by product type.
* collectionId: Filters by collection ID.



**Sample request**

Following is a sample request that can be handled by the listProducts operation.

```json
{
    "accessToken":"97c7c760cdb6a8ed800c7fdcb3337dce",
    "apiUrl":"https://wso2test-2.myshopify.com",
    "format":"json",
    "limit":"2",
    "page":"1",
    "sinceId":"400302287",
    "vendor":"Acer",
    "handle":"laptop-1",
    "productType":"Computer",
    "collectionId":"",
    "createdAfter":"2014-11-04 05:10",
    "createdBefore":"2014-11-04 05:15",
    "updatedAfter":"2014-11-04 05:10",
    "updatedBefore":"2014-11-04 05:15",
    "publishedAfter":"2014-11-04 07:15",
    "publishedBefore":"2014-11-04 07:15",
    "publishedStatus":"published",
    "fields":"id,product_type,vendor"
}
```
**Sample response**

Given below is a sample response for the listProducts operation.

```json
{
   "products":[
      {
         "id":632910392,
         "title":"IPod Nano - 8GB",
         "body_html":"<p>It's the small iPod with one very big idea: Video. Now the world's most popular music player, available in 4GB and 8GB models, lets you enjoy TV shows, movies, video podcasts, and more. The larger, brighter display means amazing picture quality. In six eye-catching colors, iPod nano is stunning all around. And with models starting at just $149, little speaks volumes.</p>",
         "vendor":"Apple",
         "product_type":"Cult Products",
         "created_at":"2018-10-31T13:02:19-04:00",
         "handle":"ipod-nano",
         "updated_at":"2018-10-31T13:02:19-04:00",
         "published_at":"2007-12-31T19:00:00-05:00",
         "template_suffix":null,
         "tags":"Emotive, Flash Memory, MP3, Music",
         "published_scope":"web",
         "admin_graphql_api_id":"gid://shopify/Product/632910392",
         "variants":[
            {
               "id":808950810,
               "product_id":632910392,
               "title":"Pink",
               "price":"199.00",
               "sku":"IPOD2008PINK",
               "position":1,
               "inventory_policy":"continue",
               "compare_at_price":null,
               "fulfillment_service":"manual",
               "inventory_management":"shopify",
               "option1":"Pink",
               "option2":null,
               "option3":null,
               "created_at":"2018-10-31T13:02:19-04:00",
               "updated_at":"2018-10-31T13:02:19-04:00",
               "taxable":true,
               "barcode":"1234_pink",
               "grams":567,
               "image_id":562641783,
               "weight":1.25,
               "weight_unit":"lb",
               "inventory_item_id":808950810,
               "inventory_quantity":10,
               "old_inventory_quantity":10,
               "requires_shipping":true,
               "admin_graphql_api_id":"gid://shopify/ProductVariant/808950810",
               "presentment_prices":[
                  {
                     "price":{
                        "currency_code":"USD",
                        "amount":"199.00"
                     },
                     "compare_at_price":null
                  }
               ]
            }
         ]
      }
   ]
}
```

**Related Shopify documentation**

[https://help.shopify.com/en/api/reference/products/product#index](https://help.shopify.com/en/api/reference/products/product#index)

#### Retrieving a list of product variants

The listProductVariants operation retrieves a list of product variants.

**listProductVariants**
```xml
<shopify.listProductVariants>
    <productId>{$ctx:productId}</productId>
    <limit>{$ctx:limit}</limit>
    <page>{$ctx:page}</page>
    <sinceId>{$ctx:sinceId}</sinceId>
    <fields>{$ctx:fields}</fields>
</shopify.listProductVariants>
```
**Properties**
* productId: A unique product ID to retrieve variants.
* limit: The limit specifies the number of results; defaults to "50".
* page: The page specifies the page to show; defaults to "1".
* fields: The comma-separated list of fields which specifies the response fields.
* sinceId: A product variant identifier. The response will only list the products having identifiers higher than this.

**Sample request**

Following is a sample request that can be handled by the listProductVariants operation.

```json
{
    "accessToken":"97c7c760cdb6a8ed800c7fdcb3337dce",
    "apiUrl":"https://wso2test-2.myshopify.com",
    "format":"json",
    "productId":"400302843",
    "limit":"2",
    "page":"1",
    "sinceId":"943278507",
    "fields":"id,barcode,price"
}
```
**Sample response**

Given below is a sample response for the listProductVariants operation.

```json
{
   "variants":[
      {
         "id":808950810,
         "product_id":632910392,
         "title":"Pink",
         "price":"199.00",
         "sku":"IPOD2008PINK",
         "position":1,
         "inventory_policy":"continue",
         "compare_at_price":null,
         "fulfillment_service":"manual",
         "inventory_management":"shopify",
         "option1":"Pink",
         "option2":null,
         "option3":null,
         "created_at":"2018-10-31T10:46:53-04:00",
         "updated_at":"2018-10-31T10:46:53-04:00",
         "taxable":true,
         "barcode":"1234_pink",
         "grams":567,
         "image_id":562641783,
         "weight":1.25,
         "weight_unit":"lb",
         "inventory_item_id":808950810,
         "inventory_quantity":10,
         "old_inventory_quantity":10,
         "requires_shipping":true,
         "admin_graphql_api_id":"gid://shopify/ProductVariant/808950810",
         "presentment_prices":[
            {
               "price":{
                  "currency_code":"USD",
                  "amount":"199.00"
               },
               "compare_at_price":null
            }
         ]
      }
   ]
}
```

**Related Shopify documentation**

[https://help.shopify.com/en/api/reference/products/product_variant#index](https://help.shopify.com/en/api/reference/products/product_variant#index)

### Sample configuration

Following example illustrates how to connect to Shopify with the init operation and createProduct operation.

1. Create a sample proxy as below :

```xml
<?xml version="1.0" encoding="UTF-8"?>
<proxy xmlns="http://ws.apache.org/ns/synapse"
       name="createProduct"
       transports="https,http"
       statistics="disable"
       trace="disable"
       startOnLoad="true">
   <target>
      <inSequence>
         <property name="accessToken" expression="json-eval($.accessToken)"/>
         <property name="apiUrl" expression="json-eval($.apiUrl)"/>
         <property name="format" expression="json-eval($.format)"/>
         <property name="product" expression="json-eval($.product)"/>
         <shopify.init>
            <accessToken>{$ctx:accessToken}</accessToken>
            <apiUrl>{$ctx:apiUrl}</apiUrl>
            <format>{$ctx:format}</format>
         </shopify.init>
         <shopify.createProduct>
            <product>{$ctx:product}</product>
         </shopify.createProduct>
         <respond/>
      </inSequence>
      <outSequence>
         <send/>
      </outSequence>
   </target>
   <description/>
</proxy>
```

2. Create a json file named createProduct.json and copy the configurations given below to it:

```json
{
    "accessToken":"97c7c760cdb6a8ed800c7fdcb3337dce",
    "apiUrl":"https://wso2test-2.myshopify.com",
    "format":"json",
    "product": {
        "title": "Burton Custom Freestyle 151",
        "body_html": "<strong>Good snowboard!</strong>",
        "vendor": "Burton",
        "product_type": "Snowboard",
        "description": "Experience the mystery!",
        "tags": "Barnes & Noble, John's Fav, \"Big Air\"",
        "published": true,
        "variants": [
              {
                "option1": "First",
                "price": "10.00",
                "sku": 123
              },
              {
                "option1": "Second",
                "price": "20.00",
                "sku": "123"
              }
        ],
        "images": [
            {
                    "attachment": "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"
            }
            ],
            "metafields": [
            {
                 "key": "new",
                 "value": "newvalue",
                 "value_type": "string",
                 "namespace": "global"
                }
            ]
    }
}
```
3. Replace the credentials with your values.

4. Execute the following curl command:

```bash
curl http://localhost:8280/services/createProduct -H "Content-Type: application/json" -d @createProduct.json
```

5. Shopify returns a json response similar to the one shown below:
 
```json
{
  "product": {
    "id": 1071559620,
    "title": "Burton Custom Freestyle 151",
    "body_html": "<strong>Good snowboard!</strong>",
    "vendor": "Burton",
    "product_type": "Snowboard",
    "created_at": "2018-10-31T13:11:20-04:00",
    "handle": "burton-custom-freestyle-151",
    "updated_at": "2018-10-31T13:11:20-04:00",
    "published_at": "2018-10-31T13:11:20-04:00",
    "template_suffix": null,
    "tags": "&quot;Big Air&quot;, Barnes & Noble, John's Fav",
    "published_scope": "web",
    "admin_graphql_api_id": "gid://shopify/Product/1071559620",
    "variants": [
      {
        "id": 1070325073,
        "product_id": 1071559620,
        "title": "Default Title",
        "price": "0.00",
        "sku": "",
        "position": 1,
        "inventory_policy": "deny",
        "compare_at_price": null,
        "fulfillment_service": "manual",
        "inventory_management": null,
        "option1": "Default Title",
        "option2": null,
        "option3": null,
        "created_at": "2018-10-31T13:11:20-04:00",
        "updated_at": "2018-10-31T13:11:20-04:00",
        "taxable": true,
        "barcode": null,
        "grams": 0,
        "image_id": null,
        "weight": 0.0,
        "weight_unit": "lb",
        "inventory_item_id": 1070325081,
        "inventory_quantity": 0,
        "old_inventory_quantity": 0,
        "requires_shipping": true,
        "admin_graphql_api_id": "gid://shopify/ProductVariant/1070325073",
        "presentment_prices": [
          {
            "price": {
              "currency_code": "USD",
              "amount": "0.00"
            },
            "compare_at_price": null
          }
        ]
      }
    ],
    "options": [
      {
        "id": 1022828690,
        "product_id": 1071559620,
        "name": "Title",
        "position": 1,
        "values": [
          "Default Title"
        ]
      }
    ],
    "images": [],
    "image": null
  }
}
```
