# Introduction

Welcome to the Convictional Commerce API. You can use our API to access various endpoints. Our API allows you to get orders and post tracking numbers, inventory and product information as needed. We provide various examples on the right, with documentation in the middle and search on the left.

If you have any feedback, let us know at feedback@convictional.com.

If you need developer support, please email support@convictional.com.

# Authentication

Convictional uses API keys  to allow access to the API. When you register your account, we generate a secure API key unique to you.

To find your key, login to Convictional and go to "Settings".

Convictional expects your API key to be included in the query when you make requests.

Example URL:
https://app.convictional.com/api/v1/example?api_key=(APIKEY)&shop=customername

<aside class="notice">
You must replace <code>(APIKEY)</code> with your personal API key.
</aside>

# Endpoints

## Mandatory Query Parameters

Parameter | Description
--------- | -----------
api_key | Your API key
company_id | Your company ID

<aside class="success">
Remember — both parameters are mandatory in every API call!
</aside>

## GET - Orders
> This command returns JSON structured like this:

```json
{
  "orders": {
    "123456789": {
      "order_id": "123456789",
      "order_name": "#1001",
      "order_partner": "partnershop",
      "order_shipping_address": {
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
      "order_line_items": {
        "id": "123456789",
        "product_id": "987654321",
        "quantity": "1",
        "sku": "SH123L",
        "variant_id": "SH123L-M"
      },
      "order_date": "2008-01-10T11:00:00-05:00",
      "order_posted": "true",
      "order_complete": "false",
      "order_tracking_numbers": "null",
      "order_companyId": "example"
    },
    "987654321": {
      etc.
    }
  }
}
```

This endpoint retrieves all orders.

### Endpoint URL

`https://app.convictional.com/api/v1/orders`

### HTTP Request Example

`GET https://app.convictional.com/api/v1/orders?api_key=(APIKEY)&shop=example`

### Order properties

Property | Description
--------- | -----------
order_id | Shopify order ID
order_name | Shopify order name
order_partner | The trading partner this order came from
order_shipping_address | Shipping address for the order
order_line_items | Line items for the order
order_date | Create date of the order
order_posted | If the order has been loaded into your system yet. Defaults to false.
order_complete | If the order has been fulfilled and tracking number sent
order_companyId | Your company ID

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

`POST https://app.convictional.com/api/v1/tracking_numbers?api_key=(APIKEY)&shop=example`

### Tracking number properties

Property | Description
--------- | -----------
order_id | Shopify order ID
tracking_number | The tracking number for the order

## POST - Products

> This command requires JSON structured like this:

```json
{
  "products": {
    "123456789": {
      "product_code": "123456789",
      "product_id": "123456789",
      "product_variants": {
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
      "product_active": "true",
      "product_description": "A product",
      "product_vendor": "example",
      "product_stock": "0"
    },
    "987654321": {
      
    }
  }
}
```

This endpoint posts product information.

### Endpoint URL

`https://app.convictional.com/api/v1/products`

### HTTP Request Example

`POST https://app.convictional.com/api/v1/products?api_key=(APIKEY)&shop=example`

### Product properties

Property | Description
--------- | -----------
product_code | Your product code
product_id | Shopify product ID
product_variants | Variant(s) of this product and their data
variant_id | The ID for this variant
variant_stock | Number of units in stock for this variant
variant_description | A consumer freindly description of this variant
product_active | Do you want to sync this product with customers? Defaults to "true"
product_description | A consumer friendly description of this product
product_vendor | A consumer friendly description of the manufacturer
product_stock | Number of units in stock if no variants setup

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

`POST https://app.convictional.com/api/v1/inventory?api_key=(APIKEY)&shop=example`

### Inventory properties
Property | Description
--------- | -----------
product_id | Your product ID. Contains two fields: variant_id and variant_stock
product_stock | Number of units in stock if no variants setup
variant_id | The ID for the variant(s)
variant_stock | Number of units in stock for each variant of the product

