# Prices

REST endpoints that allow you to create, retrieve, update and delete prices.

## Price Properties

| Property      | Type      | Required  | Description                                   |
| ------------  | --------- | ----------| --------------------------------------------- |
| \_id          | String    | Automatic <td style="width:100%;"> ID of this record  </td>
| code          | String    | Required  | Code in your system                           |
| listName      | String    | Required  | Name of this price list                       |
| startDate     | String    | Optional  | Start date (in ISO8601 format)                |
| endDate       | String    | Optional  | End date (in ISO8601 format)                  |
| currencyName  | String    | Optional  | Name of the currency                          |
| conversion    | Number    | Optional  | Conversion rate from base (default "1")       |
| markup        | Number    | Optional  | Markup percentage (default "100")             |
| rounding      | String    | Optional  | Decimals on the prices ("00" is $10.00)       |
| list          | Array     | Required  | sku, base price, markup, markup type          |
| custom        | Array     | Optional  | Custom key/value pairs                        |
| live          | Boolean   | Automatic | True for live mode, false for test mode       |
| created       | Date      | Automatic | Date record was created (in ISO8601 format)   |
| updated       | Date      | Automatic | Date record was updated (in ISO8601 format)   |
| companyId     | String    | Automatic | Your company ID                               |

## Get Price

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
      "sku": "123",
      "price": 9.99,
      "markup": 10,
      "type": "fixed"
    },
    {
      "sku": "321",
      "price": 19.99,
      "markup": 120,
      "type": "percent" },
  ],
  "created": "2018-02-12T15:14:27.147-0500",
  "updated": "2018-02-12T15:14:27.147-0500",
  "live": true,
  "companyId": "convictional-wholesale"
}
```

This endpoint returns a single price by ID.

### Endpoint

`https://api.convictional.com/prices/:id`

### Request example

`GET https://api.convictional.com/prices/5a692f658f6d524e8282dac7`

## Get Prices (bulk)

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
        "sku": "123",
        "price": 9.99,
        "markup": 10,
        "type": "fixed"
      },
      {
        "sku": "321",
        "price": 19.99,
        "markup": 120,
        "type": "percent"
      }
    ],
    "created": "2018-02-12T15:14:27.147-0500",
    "updated": "2018-02-12T15:14:27.147-0500",
    "live": true,
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
        "sku": "456",
        "price": 9.99,
        "markup": 10,
        "type": "fixed"
      },
      {
        "sku": "678",
        "price": 19.99,
        "markup": 120,
        "type": "percent"
      },
    ],
    "created": "2018-02-12T15:14:27.147-0500",
    "updated": "2018-02-12T15:14:27.147-0500",
    "live": true,
    "companyId": "convictional-wholesale"
  }
]
```

This endpoint returns all your prices.

### Endpoint

`https://api.convictional.com/prices`

### Open example

`GET https://api.convictional.com/prices`

### Filtered example

`GET https://api.convictional.com/prices?createdBefore=2018-02-28T11:26:43.000-0500`

### Query Parameters

| Property      | Type      | Required  | Description                                       |
| ------------  | --------- | ----------| --------------------------------------------------|
| fields        | String    | Optional  | Return only the specified fields, comma separated |
| page          | Number    | Optional  | Return only records on a specific page            |
| limit         | Number    | Optional  | Return up to this number of records               |
| count         | Boolean   | Optional  | Return a count of documents, defaults to false    |
| listName      | String    | Optional  | Filter by name. Returns any list containing string|
| createdBefore | Date      | Optional  | Filter records created before this date (ISO8601) |
| createdAfter  | Date      | Optional  | Filter records created after this date (ISO8601)  |
| updatedBefore | Date      | Optional  | Filter records updated before this date (ISO8601) |
| updatedAfter  | Date      | Optional  | Filter records updated after this date (ISO8601)  |

## Create Price

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
      "sku": "123",
      "price": 9.99,
      "markup": 10,
      "type": "fixed"
    },
    {
      "sku": "321",
      "price": 19.99,
      "markup": 120,
      "type": "percent"
    },
  ],
  "live": true
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
      "sku": "123",
      "price": 9.99,
      "markup": 10,
      "type": "fixed"
    },
    {
      "sku": "321",
      "price": 19.99,
      "markup": 120,
      "type": "percent"
    },
  ],
  "created": "2018-02-12T15:14:27.147-0500",
  "updated": "2018-02-12T15:14:27.147-0500",
  "live": true,
  "companyId": "convictional-wholesale"
}
```

This endpoint creates a new price.

### Endpoint

`https://api.convictional.com/prices`

### Request example

`POST https://api.convictional.com/prices`

## Create Prices (bulk)

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
          "sku": "123",
          "price": 9.99,
          "markup": 10,
          "type": "fixed"
        },
        {
          "sku": "321",
          "price": 19.99,
          "markup": 120,
          "type": "percent"
        },
      ],
      "live": true
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
          "sku": "456",
          "price": 9.99,
          "markup": 10,
          "type": "fixed"
        },
        {
          "sku": "678",
          "price": 19.99,
          "markup": 120,
          "type": "percent"
        },
      ],
      "live": true
    }
  ]
}
```

> Returns (JSON):

```json
{
  "0": "5a8755c66affcc608657ed2c",
  "1": "5a8755c66affcc608657ed2d"
}
```

This endpoint creates multiple new prices. Occurs automatically when you pass an array of price objects to this endpoint.

### Endpoint

`https://api.convictional.com/prices`

### Request example

`POST https://api.convictional.com/prices`

## Update Price

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
      "sku": "123",
      "price": 9.99,
      "markup": 10,
      "type": "fixed"
    },
    {
      "sku": "321",
      "price": 19.99,
      "markup": 120,
      "type": "percent"
    },
  ],
  "created": "2018-02-12T15:14:27.147-0500",
  "updated": "2018-02-12T15:14:27.147-0500",
  "live": true,
  "companyId": "convictional-wholesale"
}
```

This endpoint updates a single price by ID.

### Endpoint

`https://api.convictional.com/prices/:id`

### Request example

`PUT https://api.convictional.com/prices/5a692f658f6d524e8282dac8`

## Update Prices (bulk)

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
          "sku": "123",
          "price": 9.99,
          "markup": 10,
          "type": "fixed"
        },
        {
          "sku": "321",
          "price": 19.99,
          "markup": 120,
          "type": "percent"
        },
      ],
      "live": true
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
          "sku": "456",
          "price": 9.99,
          "markup": 10,
          "type": "fixed"
        },
        {
          "sku": "678",
          "price": 19.99,
          "markup": 120,
          "type": "percent"
        },
      ],
      "live": true
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

## Delete Price

> Returns (JSON):

```json
{
  "Deleted": 1
}
```

This endpoint deletes a single price by ID.

### Endpoint

`https://api.convictional.com/prices/:id`

### Request example

`DELETE https://api.convictional.com/prices/5a692f658f6d524e8282dac7`