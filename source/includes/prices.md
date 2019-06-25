# Prices

REST endpoints that allow you to create, retrieve, update and delete prices.

## Price Properties

| Property      | Type      | Required  | Description                                   |
| ------------  | --------- | ----------| --------------------------------------------- |
| \_id          | String    | Automatic <td style="width:100%;"> ID of this record  </td>
| listName      | String    | Required  | Name of this price list                       |
| currencyName  | String    | Optional  | Currency code (in ISO4217 format)             |
| conversion    | Number    | Optional  | Conversion rate from base (default "1")       |
| rounding      | String    | Optional  | Decimals on the prices ("00" is $10.00)       |
| list          | Array     | Required  | An array containing list items                |
| custom        | Array     | Optional  | Custom key/value pairs                        |
| live          | Boolean   | Automatic | True for live mode, false for test mode       |
| created       | Date      | Automatic | Date record was created (in ISO8601 format)   |
| updated       | Date      | Automatic | Date record was updated (in ISO8601 format)   |
| companyId     | String    | Automatic | Your company ID                               |

### List Item Properties

| Property      | Type      | Required  | Description                                   |
| ------------  | --------- | ----------| --------------------------------------------- |
| \_id          | String    | Automatic <td style="width:100%;"> ID of this record  </td>
| sku           | String    | Required  | The SKU of the variant to price               |
| price         | Number    | Required  | The base (wholesale) price of the item        |
| markup        | Number    | Required  | The markup, to arrive at final price          |
| minUnits      | Number    | Optional  | The minimum units ordered for this discount   |
| type          | String    | Required  | The markup type ('fixed' or 'percent')        |

## Get Price by ID

> Returns (JSON):

```json
{
  "_id": "5a692f658f6d524e8282dac7",
  "listName": "Price List for USA",
  "currencyName": "USD",
  "conversion": 1.2,
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

## Get Prices by Query

> Returns (JSON):

```json
[
  {
    "_id": "5a692f658f6d524e8282dac7",
    "listName": "Price List for USA",
    "currencyName": "USD",
    "conversion": 1.2,
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
    "listName": "Price List for Canada",
    "currencyName": "CAD",
    "conversion": 1,
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
| live          | Boolean   | Optional  | Filter by live mode status (true or false)        |

## Create Price

> Request Body (JSON):

```json
{
  "listName": "Price List for Canada",
  "currencyName": "CAD",
  "conversion": 1,
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
  "listName": "Price List for Canada",
  "currencyName": "CAD",
  "conversion": 1,
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

## Update Price

> Request Body (JSON):

```json
{
  "rounding": "00",
}
```

> Returns (JSON):

```json
{
  "_id": "5a692f658f6d524e8282dac8",
  "listName": "Price List for Canada",
  "currencyName": "CAD",
  "conversion": 1,
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

## Bulk Update/Create

> Request Body (JSON):

```json
{
  "prices": [
    {
      "listName": "Price List for USA",
      "currencyName": "USD",
      "conversion": 1.2,
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
      "listName": "Price List for Canada",
      "currencyName": "CAD",
      "conversion": 1,
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
  "updated": 2
}
```

This endpoint updates (or creates) prices. If the list name matches an existing record, it will update. Otherwise, it will create.

### Endpoint

`https://api.convictional.com/prices`

### Request example

`PUT https://api.convictional.com/prices`

## Delete Price

> Returns (JSON):

```json
{
  "deleted": 1
}
```

This endpoint deletes a single price by ID.

### Endpoint

`https://api.convictional.com/prices/:id`

### Request example

`DELETE https://api.convictional.com/prices/5a692f658f6d524e8282dac7`