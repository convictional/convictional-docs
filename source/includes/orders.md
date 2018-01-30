# Orders
The orders endpoints are REST endpoints that allow you to create, retrieve, update and delete orders.

## Order Properties
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

> Returns (JSON):

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
  "companyId": "convictional-wholesale"
}
```
This endpoint returns a single order by ID.

### Endpoint
`https://api.convictional.com/orders/:id`

### Request example
`GET https://api.convictional.com/orders/5a692f658f6d524e8282dac7`

## GET - Orders

> Returns (JSON):

```json
[
  {
    "_id": "5a692f658f6d524e8282dac7",
    "code": "12345",
    "billed": true,
    "complete": true,
    "posted": true,
    "partner": "convictional-dropshipper-us",
    "date": "2018-01-28 16:46:13",
    "items": [],
    "fulfillments": [],
    "addresses": [],
    "returns": [],
    "companyId": "convictional-wholesale"
  },
  {
    "_id": "5a692f658f6d524e8282dac8",
    "code": "12346",
    "billed": true,
    "complete": false,
    "posted": false,
    "partner": "convictional-dropshipper-ca",
    "date": "2018-01-31 13:23:13",
    "items": [],
    "fulfillments": [],
    "addresses": [],
    "returns": [],
    "companyId": "convictional-wholesale"
  }
]
```
This endpoint returns all your orders.

### Endpoint
`https://api.convictional.com/orders`

### Request example
`GET https://api.convictional.com/orders`

## POST - Order

> Request Body (JSON):

```json
{
  "code": "12345",
  "partner": "convictional-dropshipper-us",
  "date": "2018-01-28 16:46:13",
  "items": [],
  "addresses": [],
}
```
> Returns (JSON):

```json
{
  "_id": "5a692f658f6d524e8282dac7",
  "code": "12345",
  "billed": false,
  "complete": false,
  "posted": false,
  "partner": "convictional-dropshipper-us",
  "date": "2018-01-28 16:46:13",
  "items": [],
  "fulfillments": [],
  "addresses": [],
  "returns": [],
  "companyId": "convictional-wholesale"
}
```

This endpoint creates a new order.

### Endpoint
`https://api.convictional.com/orders`

### Request example
`POST https://api.convictional.com/orders`

## PUT - Order

> Request Body (JSON):

```json
{
  "complete": true
}
```

> Returns (JSON):

```json
{
  "_id": "5a692f658f6d524e8282dac7",
  "code": "12345",
  "billed": true,
  "complete": true,
  "posted": true,
  "partner": "convictional-dropshipper-us",
  "date": "2018-01-28 16:46:13",
  "items": [],
  "fulfillments": [],
  "addresses": [],
  "returns": [],
  "companyId": "convictional-wholesale"
}
```
This endpoint updates a single order by ID.

### Endpoint
`https://api.convictional.com/orders/:id`

### Request example
`PUT https://api.convictional.com/orders/5a692f658f6d524e8282dac7`

## PUT - Orders

> Request Body (JSON):

```json
{
  "orders": [
    {
      "code": "12345",
      "billed": true,
      "complete": true,
      "posted": true,
      "partner": "convictional-dropshipper-us",
      "date": "2018-01-28 16:46:13",
      "items": [],
      "fulfillments": [],
      "addresses": [],
      "returns": []
    },
    {
      "code": "12346",
      "billed": true,
      "complete": false,
      "posted": false,
      "partner": "convictional-dropshipper-ca",
      "date": "2018-01-31 13:23:13",
      "items": [],
      "fulfillments": [],
      "addresses": [],
      "returns": [],
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
    "billed": true,
    "complete": true,
    "posted": true,
    "partner": "convictional-dropshipper-us",
    "date": "2018-01-28 16:46:13",
    "items": [],
    "fulfillments": [],
    "addresses": [],
    "returns": [],
    "companyId": "convictional-wholesale"
  },
  {
    "_id": "5a692f658f6d524e8282dac8",
    "code": "12346",
    "billed": true,
    "complete": false,
    "posted": false,
    "partner": "convictional-dropshipper-ca",
    "date": "2018-01-31 13:23:13",
    "items": [],
    "fulfillments": [],
    "addresses": [],
    "returns": [],
    "companyId": "convictional-wholesale"
  }
]
```

This endpoint bulk updates (or creates) orders.

### Endpoint
`https://api.convictional.com/orders`

### Request example
`PUT https://api.convictional.com/orders`

## DELETE - Order

> Returns (JSON):

```json
{
  "5a692f658f6d524e8282dac7"
}
```
This endpoint deletes a single order by ID.

### Endpoint
`https://api.convictional.com/orders/:id`

### Request example
`DELETE https://api.convictional.com/orders/5a692f658f6d524e8282dac7`