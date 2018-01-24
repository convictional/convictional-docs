# Introduction

Welcome to the Convictional Commerce API. You can use our API to access various resources. We provide various examples on the right, with documentation in the middle and search on the left. 

# Authentication

Convictional uses API keys to authenticate you. When you register your account, we generate a secure API key unique to you. To find your key, login to Convictional and go to "Settings".

Convictional expects your API key to be included in the query when you make requests.

Example URL:
https://app.convictional.com/api/v1/example?api_key=(APIKEY)

<aside class="notice">
You must replace <code>(APIKEY)</code> with your personal API key.
</aside>

# Endpoints

## GET - Orders
> This command returns JSON structured like this:

```json
{
  "orders": {
    "123456789": {
      "id": "123456789",
      "name": "#1001",
      "partner": "partnershop",
      "shipping_address": {
        "address1": "123 Example St",
        "address2": "",
        "city": "Waterloo",
        "company": null,
        "country": "Canada",
        "first_name": "Ryan",
        "last_name": "Reymonds",
        "province": "Ontario",
        "zip": "N2L5L5",
        "name": "Ryan Reymonds",
        "country_code": "CA",
        "province_code": "ON"
      },
      "line_items": {
        "id": "123456789",
        "product_id": "987654321",
        "quantity": "1",
        "sku": "SH123L",
        "variant_id": "SH123L-M"
      },
      "date": "2008-01-10T11:00:00-05:00",
      "posted": "true",
      "complete": "false",
      "fulfillments": [],
      "trackingNumber": "1234",
      "companyId": "example"
    }
  }
}
```

This endpoint retrieves all orders.

### Endpoint URL

`https://app.convictional.com/api/v1/orders`

### HTTP Request Example

`GET https://app.convictional.com/api/v1/orders?api_key=(APIKEY)`

### Order properties

Property | Description
--------- | -----------
id | Shopify order ID
name | Shopify order name
partner | The trading partner this order came from
shippingAddress | Shipping address for the order
items | Line items for the order
date | Create date of the order
posted | If the order has been loaded into your system yet. Defaults to false.
complete | If the order has been fulfilled and tracking number sent
companyId | Your company ID

## POST - Tracking Numbers

> This command requires JSON structured like this:

```json
{
  "tracking_numbers": {
    "12345": "g4231hjk4",
    "54321": "fhj43123h"
  }
}
```

This endpoint posts tracking numbers to orders.

### Endpoint URL

`https://app.convictional.com/api/v1/tracking_numbers`

### HTTP Request Example

`POST https://app.convictional.com/api/v1/tracking_numbers?api_key=(APIKEY)`

### Tracking number properties

Property | Description
--------- | -----------
id | Shopify order ID
tracking_number | The tracking number for the order

## POST - Products

> This command requires JSON structured like this:

```json
{
  "products": {
    "123456789": {
      "code": "123456789",
      "id": "123456789",
      "variants": {
        "123": {
          "variant_id": "123",
          "variant_stock": "3",
          "variant_description": "A variant"
        },
        "456": {
          "variant_id": "456",
          "variant_stock": "7",
          "variant_description": "Another variant"
        }
      },
      "active": "true",
      "description": "A product",
      "vendor": "example",
      "stock": "0"
    }
  }
}
```

This endpoint posts product information.

### Endpoint URL

`https://app.convictional.com/api/v1/products`

### HTTP Request Example

`POST https://app.convictional.com/api/v1/products?api_key=(APIKEY)`

### Product properties

Property | Description
--------- | -----------
code | Your product code
id | Shopify product ID
variants | Variant(s) of this product and their data
variant_id | The ID for this variant
variant_stock | Number of units in stock for this variant
variant_description | A consumer freindly description of this variant
active | Do you want to sync this product with customers? Defaults to "true"
description | A consumer friendly description of this product
vendor | A consumer friendly description of the manufacturer
stock | Number of units in stock if no variants setup

## POST - Inventory

> This command requires JSON structured like this:

```json
{
  "inventory": {
    "123456789": {
      "123": "3",
      "456": "7",
      "789": "15"
    },
    "987654321": "5"
  }
}
```

This endpoint posts inventory to products and variants.

### Endpoint URL

`https://app.convictional.com/api/v1/inventory`

### HTTP Request Example

`POST https://app.convictional.com/api/v1/inventory?api_key=(APIKEY)`

### Inventory properties
Property | Description
--------- | -----------
id | Your product ID. Contains two fields: variant_id and variant_stock
stock | Number of units in stock if no variants setup
variant_id | The ID for the variant(s)
variant_stock | Number of units in stock for each variant of the product

## POST - X12 EDI Translate

> This command returns JSON structured like this:

```json
{
  "segmentID": {
    "0": "value",
    "1": "value"
  },
  "segmentID": [
    {
      "0": "value",
      "1": "value"
    },
    {
      "0": "value",
      "1": "value"
    }
  ]
}
```

This endpoint allows you to convert an X12 EDI document in raw text into JSON.

### Endpoint URL

`https://api.convictional.com/translate`

### HTTP Request example

`POST https://api.convictional.com/translate`

<aside class="notice">
Include your API key in the "Authorization" header to authenticate your request.
</aside>

### Properties
Property | Description
--------- | -----------
body | The body of the request must contain an X12 EDI document in plain text.

