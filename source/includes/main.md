# Introduction

> API Endpoint:

```json
https://api.convictional.com
```

Welcome to the Convictional Commerce API documentation. You can use our API to access various resources on the Convictional platform. We provide various examples on the right, with documentation in the middle and search on the left. We use this API and this documentation every day to build our own applications, so we build it to be as easy to use, stable and scalable as we can.

Our goal providing an API for our service is to allow technically inclined customers to take advantage of the infrastructure, business rules, integrations and admin capabilities of our platform. Almost anything you can do in the admin, you can do here too.

Our API is still on the first version. When version changes happen in the future, we will notify users and migrate you to the new version with an appropriate grace period. If you have any feedback, please get in touch and let us know. We are always open to adding new endpoints to make it as easy as possible for our customers to trade with their partners. 

# Authentication
Convictional uses API keys to authenticate your requests. When you register your account, we generate an API key for you. To find your key, login to Convictional and go to "Settings". Include your API key in the "Authorization" header to authenticate your request.

# Errors
> Example response: 

```json
{
  "Not authorized"
}

```

The Convictional API uses the following error codes:

Code | Description
---------- | -------
401 | Not authorized
500 | Bad request

# Orders
The orders endpoints are REST endpoints that allow you to create, retrieve, update and delete orders.

## Properties
Property | Type | Description | Required Fields
----------- | ----------- |  -----------  |  -----------
\_id | String | ID of this record in Convictional | Automatic
code | String | Order number in the source ecommerce system | Automatic
billed | Boolean | Has this order been invoiced? | Automatic
complete | Boolean | Is this order shipped and billed? | Automatic
posted | Boolean | Has this order been synced with your system of record? | Automatic
partner | String | The partner code that sent this order | Required
date | String | The date of the order (YY/MM/DD hh:mm:ss) | Required
items | Array | Contains all order items (products, tax, shipping) | Optional
fulfillments | Array | Contains all the shipments and tracking information | Optional
addresses | Array | Contains all the customer addresses | Optional
returns | Array | Contains any returns associated with this order | Optional
companyId | String | Your company ID in Convictional | Automatic

## GET - Order
```json
{
  "_id": "5a692f658f6d524e8282dac7",
  "code": "12345",
  "billed": true,
  "complete": true,
  "posted": true,
  "partner": "my-partner",
  "date": "2018-01-28 16:46:13",
  "items": [],
  "fulfillments": [],
  "addresses": [],
  "returns": [],
  "companyId": "my-company"
}
```
This endpoint returns a single order by ID.

### Endpoint
`https://api.convictional.com/orders/:id`

### Request example
`GET https://api.convictional.com/orders/5a692f658f6d524e8282dac7`

## GET - Orders
```json

```
This endpoint returns all your orders.

### Endpoint
`https://api.convictional.com/orders`

### Request example
`GET https://api.convictional.com/orders`

## POST - Order
```json

```

This endpoint creates a new order.

### Endpoint
`https://api.convictional.com/orders`

### Request example
`POST https://api.convictional.com/orders`

## PUT - Order
```json

```
This endpoint updates a single order by ID.

### Endpoint
`https://api.convictional.com/orders/:id`

### Request example
`PUT https://api.convictional.com/orders/5a692f658f6d524e8282dac7`

## DELETE - Order
```json

```
This endpoint deletes a single order by ID.

### Endpoint
`https://api.convictional.com/orders/:id`

### Request example
`DELETE https://api.convictional.com/orders/5a692f658f6d524e8282dac7`

# Products
The products endpoints are REST endpoints that allow you to create, retrieve, update and delete products.

## Properties
Property | Type | Description | Required Field
----------- | ----------- |  -----------  |  -----------
\_id | String | ID of this record in Convictional | Automatic
code | String | The product code in your system of record | Required
active | Boolean | Is this product active currently? | Required
bodyHtml | String | The HTML for the ecommerce pages | Optional
images | Array | An array of image information | Optional
tags | String | Comma separated tags ('summer, beauty, toronto') | Optional
title | String | The product title | Required
type | String | The product type ('item', 'tax', 'shipping') | Required
variants | Array | An array of variants of the product | Required
vendor | String | The brand (or your company name if you are a brand) | Optional
companyId | String | Your company ID in Convictional | Automatic

## GET - Product
```json

```
This endpoint returns a single product by ID.

### Endpoint
`https://api.convictional.com/products/:id`

### Request example
`GET https://api.convictional.com/products/5a692f658f6d524e8282dac7`

## GET - Products
```json

```
This endpoint returns all your products.

### Endpoint
`https://api.convictional.com/products`

### Request example
`GET https://api.convictional.com/products`

## POST - Product
```json

```

This endpoint creates a new product.

### Endpoint
`https://api.convictional.com/products`

### Request example
`POST https://api.convictional.com/products`

## PUT - Product
```json

```
This endpoint updates a single product by ID.

### Endpoint
`https://api.convictional.com/products/:id`

### Request example
`PUT https://api.convictional.com/products/5a692f658f6d524e8282dac7`

## DELETE - Product
```json

```
This endpoint deletes a single product by ID.

### Endpoint
`https://api.convictional.com/products/:id`

### Request example
`DELETE https://api.convictional.com/products/5a692f658f6d524e8282dac7`

# Partners
The partners endpoints are REST endpoints that allow you to create, retrieve, update and delete partners.

## Properties
Property | Type | Description | Required Field
----------- | ----------- |  -----------  |  -----------
\_id | String | ID of this record in Convictional | Automatic
code | String | The partner code in your system of record | Required
active | Boolean | Do you want to sync with this partner? | Required
email | String | The main contact email for this partner | Required
invited | Boolean | Have they been invited? | Automatic
itemLookup | Array | A reference of your item codes and theirs | Optional
priceList | String | The name of their price list | Optional
relationship | String | Your relationship to them. 'parent', 'child' or 'self' | Optional
shopName | String | Their ecommerce platform shop name | Required
companyId | String | Your company ID in Convictional | Automatic

## GET - Partner
```json

```
This endpoint returns a single partner by ID.

### Endpoint
`https://api.convictional.com/partners/:id`

### Request example
`GET https://api.convictional.com/partners/5a692f658f6d524e8282dac7`

## GET - Partners
```json

```
This endpoint returns all your partners.

### Endpoint
`https://api.convictional.com/partners`

### Request example
`GET https://api.convictional.com/partners`

## POST - Partner
```json

```

This endpoint creates a new partner.

### Endpoint
`https://api.convictional.com/partners`

### Request example
`POST https://api.convictional.com/partners`

## PUT - Partner
```json

```
This endpoint updates a single partner by ID.

### Endpoint
`https://api.convictional.com/partners/:id`

### Request example
`PUT https://api.convictional.com/partners/5a692f658f6d524e8282dac7`

## DELETE - Partner
```json

```
This endpoint deletes a single partner by ID.

### Endpoint
`https://api.convictional.com/partners/:id`

### Request example
`DELETE https://api.convictional.com/partners/5a692f658f6d524e8282dac7`

# Prices
The prices endpoints are REST endpoints that allow you to create, retrieve, update and delete prices.

## Properties
Property | Type | Description | Required Field
----------- | ----------- |  -----------  |  -----------
\_id | String | ID of this record in Convictional | Automatic
code | String | The price list code in your system of record | Required
listName | String | The name of this price list | Required
startDate | String | The start date (YY/MM/DD hh:mm:ss) | Optional
endDate | String | The end date (YY/MM/DD hh:mm:ss) | Optional
currencyName | String | The name of the currency | Optional
conversion | Number | The conversion rate from base currency ("1" for same) | Optional
markup | Number | The markup percentage ("200" is 200%) | Optional
rounding | String | The decimals on the price ("00" is $10.00) | Optional
list | Array | The price list: sku, base price, markup, markup type | Required
companyId | String | Your company ID in Convictional, auto generated | Automatic

## GET - Price
```json

```
This endpoint returns a single price by ID.

### Endpoint
`https://api.convictional.com/prices/:id`

### Request example
`GET https://api.convictional.com/prices/5a692f658f6d524e8282dac7`

## GET - Prices
```json

```
This endpoint returns all your prices.

### Endpoint
`https://api.convictional.com/prices`

### Request example
`GET https://api.convictional.com/prices`

## POST - Price
```json

```

This endpoint creates a new price.

### Endpoint
`https://api.convictional.com/prices`

### Request example
`POST https://api.convictional.com/prices`

## PUT - Price
```json

```
This endpoint updates a single price by ID.

### Endpoint
`https://api.convictional.com/prices/:id`

### Request example
`PUT https://api.convictional.com/prices/5a692f658f6d524e8282dac7`

## DELETE - Price
```json

```
This endpoint deletes a single price by ID.

### Endpoint
`https://api.convictional.com/prices/:id`

### Request example
`DELETE https://api.convictional.com/prices/5a692f658f6d524e8282dac7`

# Logs
The logs endpoints are REST endpoints that allow you to create, retrieve, update and delete logs.

## Properties
Property | Type | Description | Required Field
----------- | ----------- |  -----------  |  -----------
\_id | String | ID of this record in Convictional | Automatic
createDate | String | The date of the log (YY/MM/DD hh:mm:ss) | Required
description | String | A description of what happened | Required
companyId | String | Your company ID in Convictional | Automatic

## GET - Log
```json

```
This endpoint returns a single log by ID.

### Endpoint
`https://api.convictional.com/logs/:id`

### Request example
`GET https://api.convictional.com/logs/5a692f658f6d524e8282dac7`

## GET - Logs
```json

```
This endpoint returns all your logs.

### Endpoint
`https://api.convictional.com/logs`

### Request example
`GET https://api.convictional.com/logs`

## POST - Log
```json

```

This endpoint creates a new log.

### Endpoint
`https://api.convictional.com/logs`

### Request example
`POST https://api.convictional.com/logs`

## PUT - Log
```json

```
This endpoint updates a single log by ID.

### Endpoint
`https://api.convictional.com/logs/:id`

### Request example
`PUT https://api.convictional.com/logs/5a692f658f6d524e8282dac7`

## DELETE - Order
```json

```
This endpoint deletes a single log by ID.

### Endpoint
`https://api.convictional.com/logs/:id`

### Request example
`DELETE https://api.convictional.com/logs/5a692f658f6d524e8282dac7`

# EDI
The EDI endpoints are RPC endpoints that allow you to translate and transmit EDI documents.

## POST - Translate

> Returns JSON structured like this:

```json
{
  "segmentID": {
    "0": "first_element_value",
    "1": "second_element_value",
    "2": "third_element_value"
  },
  "segmentID": [
    {
      "0": "first_element_value",
      "1": "second_element_value",
      "2": "third_element_value"
    },
    {
      "0": "first_element_value",
      "1": "second_element_value",
      "2": "third_element_value"
    }
  ]
}
```

This endpoint allows you to convert an X12 EDI document in raw text into JSON.

### Endpoint URL

`https://api.convictional.com/translate`

### HTTP Request example

`POST https://api.convictional.com/translate`

### Properties
Property | Description
--------- | -----------
body | The body of the request must contain an X12 EDI document in plain text.

