# Prices
REST endpoints that allow you to create, retrieve, update and delete prices.

## Price Properties
| Property      | Type      | Required  | Description                                   |
| ------------  | --------- | ----------| --------------------------------------------- |
| \_id          | String    | Automatic <td style="width:100%;"> ID of this record  </td>
| code          | String    | Required  | Code in your system                           |
| listName      | String    | Required  | Name of this price list                       |
| startDate     | String    | Optional  | Start date (YY/MM/DD hh:mm:ss)                |
| endDate       | String    | Optional  | End date (YY/MM/DD hh:mm:ss)                  |
| currencyName  | String    | Optional  | Name of the currency                          |
| conversion    | Number    | Optional  | Conversion rate from base (default "1")       |
| markup        | Number    | Optional  | Markup percentage (default "100")             |
| rounding      | String    | Optional  | Decimals on the prices ("00" is $10.00)       |
| list          | Array     | Required  | sku, base price, markup, markup type          |
| created       | Date      | Automatic | Date record was created (in ISO8601 format)   |
| updated       | Date      | Automatic | Date record was updated (in ISO8601 format)   |
| companyId     | String    | Automatic | Your company ID                               |

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
  "list": [
    { 
      "code": "123", 
      "price": 9.99, 
      "markup": 10, 
      "type": "fixed" 
    },
    { 
      "code": "321", 
      "price": 19.99, 
      "markup": 120, 
      "type": "percent" },
  ],
  "created": "2018-02-12T15:14:27.147-0500",
  "updated": "2018-02-12T15:14:27.147-0500",
  "companyId": "convictional-wholesale"
}
```
This endpoint returns a single price by ID.

### Endpoint
`https://api.convictional.com/prices/:id`

### Request example
`GET https://api.convictional.com/prices/5a692f658f6d524e8282dac7`

## GET - Prices (bulk)

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
    "list": [
      { 
        "code": "123", 
        "price": 9.99, 
        "markup": 10, 
        "type": "fixed" 
      },
      { 
        "code": "321", 
        "price": 19.99, 
        "markup": 120, 
        "type": "percent" 
      },
    ],
    "created": "2018-02-12T15:14:27.147-0500",
    "updated": "2018-02-12T15:14:27.147-0500",
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
    "list": [
      { 
        "code": "456", 
        "price": 9.99, 
        "markup": 10, 
        "type": "fixed" 
      },
      { 
        "code": "678", 
        "price": 19.99, 
        "markup": 120, 
        "type": "percent" 
      },
    ],
    "created": "2018-02-12T15:14:27.147-0500",
    "updated": "2018-02-12T15:14:27.147-0500",
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
  "list": [
    { 
      "code": "123", 
      "price": 9.99, 
      "markup": 10, 
      "type": "fixed" 
    },
    { 
      "code": "321", 
      "price": 19.99, 
      "markup": 120, 
      "type": "percent" 
    },
  ]
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
  "list": [
    { 
      "code": "123", 
      "price": 9.99, 
      "markup": 10, 
      "type": "fixed" 
    },
    { 
      "code": "321", 
      "price": 19.99, 
      "markup": 120, 
      "type": "percent" 
    },
  ],
  "created": "2018-02-12T15:14:27.147-0500",
  "updated": "2018-02-12T15:14:27.147-0500",
  "companyId": "convictional-wholesale"
}
```

This endpoint creates a new price.

### Endpoint
`https://api.convictional.com/prices`

### Request example
`POST https://api.convictional.com/prices`

## POST - Prices (bulk)

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
      "list": [
        { 
          "code": "123", 
          "price": 9.99, 
          "markup": 10, 
          "type": "fixed" 
        },
        { 
          "code": "321", 
          "price": 19.99, 
          "markup": 120, 
          "type": "percent" 
        },
      ]
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
      "list": [
        { 
          "code": "456", 
          "price": 9.99, 
          "markup": 10, 
          "type": "fixed" 
        },
        { 
          "code": "678", 
          "price": 19.99, 
          "markup": 120, 
          "type": "percent" 
        },
      ]
    }
  ]
}
```

>  Returns (JSON):

```json
{
  "0": "5a8755c66affcc608657ed2c",
  "1": "5a8755c66affcc608657ed2d"
}
```
This endpoint creates multiple new prices. Occurs automatically when you pass an array of price objects to this endpoint.

### Endpoint
`https://api.convictional.com/prices`

### Request Example
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
  "list": [
    { 
      "code": "123", 
      "price": 9.99, 
      "markup": 10, 
      "type": "fixed" 
    },
    { 
      "code": "321", 
      "price": 19.99, 
      "markup": 120, 
      "type": "percent" 
    },
  ],
  "created": "2018-02-12T15:14:27.147-0500",
  "updated": "2018-02-12T15:14:27.147-0500",
  "companyId": "convictional-wholesale"
}
```
This endpoint updates a single price by ID.

### Endpoint
`https://api.convictional.com/prices/:id`

### Request example
`PUT https://api.convictional.com/prices/5a692f658f6d524e8282dac8`

## PUT - Prices (bulk)

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
      "list": [
        { 
          "code": "123", 
          "price": 9.99, 
          "markup": 10, 
          "type": "fixed" 
        },
        { 
          "code": "321", 
          "price": 19.99, 
          "markup": 120, 
          "type": "percent" 
        },
      ]
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
      "list": [
        { 
          "code": "456", 
          "price": 9.99, 
          "markup": 10, 
          "type": "fixed" 
        },
        { 
          "code": "678", 
          "price": 19.99, 
          "markup": 120, 
          "type": "percent" 
        },
      ]
    }
  ]
}
```

> Returns (JSON):

```json
{
  "Modified": 2
}
```
This endpoint updates (or creates) prices. If the code matches an existing record, it will update. Otherwise, it will create.

### Endpoint
`https://api.convictional.com/prices`

### Request example
`PUT https://api.convictional.com/prices`

## DELETE - Price

> Returns (JSON):

```json
OK
```
This endpoint deletes a single price by ID.

### Endpoint
`https://api.convictional.com/prices/:id`

### Request example
`DELETE https://api.convictional.com/prices/5a692f658f6d524e8282dac7`

## DELETE - Prices (bulk)

> Request Body (JSON):

```json
[
  "5a8755c66affcc608657ed2c",
  "5a8755c66affcc608657ed2d"
]
```

> Returns (JSON):

```json
{
  "Deleted": 2
}
```
This endpoint deletes multiple prices by ID.

### Endpoint
`https://api.convictional.com/prices`

### Request Example
`DELETE https://api.convictional.com/prices`