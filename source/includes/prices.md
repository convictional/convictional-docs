# Prices
The prices endpoints are REST endpoints that allow you to create, retrieve, update and delete prices.

## Price Properties
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

> Returns (JSON):

```json
{
  "_id": "5a692f658f6d524e8282dac7",
  "code": "12345",
  "listName": "Price List for USA",
  "startDate": "2018/01/01 00:00:00",
  "endDate": "2018/01/31 23:59:59",
  "currencyName": "USD",
  "conversion": 1.2,
  "markup": 120,
  "rounding": "99",
  "list": [],
  "companyId": "convictional-wholesale"
}
```
This endpoint returns a single price by ID.

### Endpoint
`https://api.convictional.com/prices/:id`

### Request example
`GET https://api.convictional.com/prices/5a692f658f6d524e8282dac7`

## GET - Prices

> Returns (JSON):

```json
[
  {
    "_id": "5a692f658f6d524e8282dac7",
    "code": "12345",
    "listName": "Price List for USA",
    "startDate": "2018/01/01 00:00:00",
    "endDate": "2018/01/31 23:59:59",
    "currencyName": "USD",
    "conversion": 1.2,
    "markup": 120,
    "rounding": "99",
    "list": [],
    "companyId": "convictional-wholesale"
  },
  {
    "_id": "5a692f658f6d524e8282dac8",
    "code": "12346",
    "listName": "Price List for Canada",
    "startDate": "2018/01/01 00:00:00",
    "endDate": "2018/01/31 23:59:59",
    "currencyName": "CAD",
    "conversion": 1,
    "markup": 100,
    "rounding": "99",
    "list": [],
    "companyId": "convictional-wholesale"
  }
]
```
This endpoint returns all your prices.

### Endpoint
`https://api.convictional.com/prices`

### Request example
`GET https://api.convictional.com/prices`

## POST - Price

> Request Body (JSON):

```json
{
  "code": "12346",
  "listName": "Price List for Canada",
  "startDate": "2018/01/01 00:00:00",
  "endDate": "2018/01/31 23:59:59",
  "currencyName": "CAD",
  "conversion": 1,
  "markup": 100,
  "rounding": "99",
  "list": [],
}
```

> Returns (JSON):

```json
{
  "_id": "5a692f658f6d524e8282dac8",
  "code": "12346",
  "listName": "Price List for Canada",
  "startDate": "2018/01/01 00:00:00",
  "endDate": "2018/01/31 23:59:59",
  "currencyName": "CAD",
  "conversion": 1,
  "markup": 100,
  "rounding": "99",
  "list": [],
  "companyId": "convictional-wholesale"
}
```

This endpoint creates a new price.

### Endpoint
`https://api.convictional.com/prices`

### Request example
`POST https://api.convictional.com/prices`

## PUT - Price

> Request Body (JSON):

```json
{
  "markup": 110,
  "rounding": "00",
}
```

> Returns (JSON):

```json
{
  "_id": "5a692f658f6d524e8282dac8",
  "code": "12346",
  "listName": "Price List for Canada",
  "startDate": "2018/01/01 00:00:00",
  "endDate": "2018/01/31 23:59:59",
  "currencyName": "CAD",
  "conversion": 1,
  "markup": 110,
  "rounding": "00",
  "list": [],
  "companyId": "convictional-wholesale"
}
```
This endpoint updates a single price by ID.

### Endpoint
`https://api.convictional.com/prices/:id`

### Request example
`PUT https://api.convictional.com/prices/5a692f658f6d524e8282dac8`

## PUT - Prices

> Request Body (JSON):

```json
{
  "prices": [
    {
      "code": "12345",
      "listName": "Price List for USA",
      "startDate": "2018/01/01 00:00:00",
      "endDate": "2018/01/31 23:59:59",
      "currencyName": "USD",
      "conversion": 1.2,
      "markup": 120,
      "rounding": "99",
      "list": [],
    },
    {
      "code": "12346",
      "listName": "Price List for Canada",
      "startDate": "2018/01/01 00:00:00",
      "endDate": "2018/01/31 23:59:59",
      "currencyName": "CAD",
      "conversion": 1,
      "markup": 100,
      "rounding": "99",
      "list": [],
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
    "listName": "Price List for USA",
    "startDate": "2018/01/01 00:00:00",
    "endDate": "2018/01/31 23:59:59",
    "currencyName": "USD",
    "conversion": 1.2,
    "markup": 120,
    "rounding": "99",
    "list": [],
    "companyId": "convictional-wholesale"
  },
  {
    "_id": "5a692f658f6d524e8282dac8",
    "code": "12346",
    "listName": "Price List for Canada",
    "startDate": "2018/01/01 00:00:00",
    "endDate": "2018/01/31 23:59:59",
    "currencyName": "CAD",
    "conversion": 1,
    "markup": 100,
    "rounding": "99",
    "list": [],
    "companyId": "convictional-wholesale"
  }
]
```

### Endpoint
`https://api.convictional.com/prices`

### Request example
`PUT https://api.convictional.com/prices`

## DELETE - Price

> Returns (JSON):

```json
{
  "5a692f658f6d524e8282dac7"
}
```
This endpoint deletes a single price by ID.

### Endpoint
`https://api.convictional.com/prices/:id`

### Request example
`DELETE https://api.convictional.com/prices/5a692f658f6d524e8282dac7`