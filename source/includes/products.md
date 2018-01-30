# Products
The products endpoints are REST endpoints that allow you to create, retrieve, update and delete products.

## Product Properties
Property | Type | Description | Required Field
----------- | ----------- |  -----------  |  -----------
\_id | String | ID of this record in Convictional | Automatic
code | String | The product code in your system of record | Required
active | Boolean | Is this product active currently? | Required
bodyHtml | String | The HTML for the ecommerce pages | Optional
images | Array | An array of image information | Optional
tags | Array | An array of tags ['summer', 'beauty'] | Optional
title | String | The product title | Required
type | String | The product type ('item', 'tax', 'shipping') | Required
variants | Array | An array of variants of the product | Required
vendor | String | The brand (or your company name if you are a brand) | Optional
companyId | String | Your company ID in Convictional | Automatic

## GET - Product

> Returns (JSON):

```json
{
  "_id": "5a692f658f6d524e8282dac7",
  "code": "12345",
  "active": true,
  "bodyHtml": "<p>Great product!</p>",
  "images": [],
  "tags": [],
  "title": "Great product",
  "type": "item",
  "variants": [],
  "vendor": "Convictional Wholesale",
  "companyId": "convictional-wholesale"
}
```
This endpoint returns a single product by ID.

### Endpoint
`https://api.convictional.com/products/:id`

### Request example
`GET https://api.convictional.com/products/5a692f658f6d524e8282dac7`

## GET - Products

> Returns (JSON):

```json
[
  {
    "_id": "5a692f658f6d524e8282dac7",
    "code": "12345",
    "active": true,
    "bodyHtml": "<p>Great product!</p>",
    "images": [],
    "tags": [],
    "title": "Great product",
    "type": "item",
    "variants": [],
    "vendor": "Convictional Wholesale",
    "companyId": "convictional-wholesale"
  },
  {
    "_id": "5a692f658f6d524e8282dac8",
    "code": "12346",
    "active": true,
    "bodyHtml": "<p>Greatest product!</p>",
    "images": [],
    "tags": [],
    "title": "Greatest product",
    "type": "item",
    "variants": [],
    "vendor": "Convictional Wholesale",
    "companyId": "convictional-wholesale"
  }
]
```
This endpoint returns all your products.

### Endpoint
`https://api.convictional.com/products`

### Request example
`GET https://api.convictional.com/products`

## POST - Product

> Request Body (JSON):

```json
{
  "code": "12345",
  "active": true,
  "bodyHtml": "<p>Great product!</p>",
  "images": [],
  "tags": [],
  "title": "Great product",
  "type": "item",
  "variants": [],
  "vendor": "Convictional Wholesale"
}
```

> Returns (JSON):

```json
{
  "_id": "5a692f658f6d524e8282dac7",
  "code": "12345",
  "active": true,
  "bodyHtml": "<p>Great product!</p>",
  "images": [],
  "tags": [],
  "title": "Great product",
  "type": "item",
  "variants": [],
  "vendor": "Convictional Wholesale",
  "companyId": "convictional-wholesale"
}
```

This endpoint creates a new product.

### Endpoint
`https://api.convictional.com/products`

### Request example
`POST https://api.convictional.com/products`

## PUT - Product

> Request Body (JSON):

```json
{
  "active": false,
  "bodyHtml": "<p>Greater product!</p>",
  "title": "Greater product"
}
```

> Returns (JSON):

```json
{
  "_id": "5a692f658f6d524e8282dac7",
  "code": "12345",
  "active": false,
  "bodyHtml": "<p>Greater product!</p>",
  "images": [],
  "tags": [],
  "title": "Greater product",
  "type": "item",
  "variants": [],
  "vendor": "Convictional Wholesale",
  "companyId": "convictional-wholesale"
}
```
This endpoint updates a single product by ID.

### Endpoint
`https://api.convictional.com/products/:id`

### Request example
`PUT https://api.convictional.com/products/5a692f658f6d524e8282dac7`

## PUT - Products

> Request Body (JSON):

```json
{
  "products": [
    {
      "code": "12345",
      "active": true,
      "bodyHtml": "<p>Great product!</p>",
      "images": [],
      "tags": [],
      "title": "Great product",
      "type": "item",
      "variants": [],
      "vendor": "Convictional Wholesale",
    },
    {
      "code": "12346",
      "active": true,
      "bodyHtml": "<p>Greatest product!</p>",
      "images": [],
      "tags": [],
      "title": "Greatest product",
      "type": "item",
      "variants": [],
      "vendor": "Convictional Wholesale",
    }
  ]
}
```

> Returns (JSON):

```json
[
  {
    "_id": "5a692f658f6d524e8282dac7",
    "code": "12345",
    "active": true,
    "bodyHtml": "<p>Great product!</p>",
    "images": [],
    "tags": [],
    "title": "Great product",
    "type": "item",
    "variants": [],
    "vendor": "Convictional Wholesale",
    "companyId": "convictional-wholesale"
  },
  {
    "_id": "5a692f658f6d524e8282dac8",
    "code": "12346",
    "active": true,
    "bodyHtml": "<p>Greatest product!</p>",
    "images": [],
    "tags": [],
    "title": "Greatest product",
    "type": "item",
    "variants": [],
    "vendor": "Convictional Wholesale",
    "companyId": "convictional-wholesale"
  }
]
```

This endpoint bulk updates (or creates) products.

### Endpoint
`https://api.convictional.com/products`

### Request example
`PUT https://api.convictional.com/products`

## DELETE - Product

> Returns (JSON):

```json
{
  "5a692f658f6d524e8282dac7"
}
```
This endpoint deletes a single product by ID.

### Endpoint
`https://api.convictional.com/products/:id`

### Request example
`DELETE https://api.convictional.com/products/5a692f658f6d524e8282dac7`