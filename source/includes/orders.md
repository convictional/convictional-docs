# Orders

REST endpoints that allow you to create, retrieve, update and delete orders.

## Order Properties

| Property      | Type      | Required  | Description                                         |
| -----------   | ------    | --------- | --------------------------------------------------- |
| \_id          | String    | Automatic <td style="width:100%;"> ID of this record        </td>
| code          | String    | Required  | Order number in the source ecommerce system         |
| parentCode    | String    | Required  | Parent prder number in the system of record         |
| posted        | Boolean   | Automatic | Has this order been synced with your system?        |
| shipped       | Boolean   | Automatic | Has this order been shipped?                        |
| billed        | Boolean   | Automatic | Has this order been invoiced?                       |
| complete      | Boolean   | Automatic | Has this order been synced to your partner?         |
| partner       | String    | Required  | The partner code that sent this order               |
| date          | String    | Required  | The date of the order (YY/MM/DD hh:mm:ss)           |
| items         | Array     | Required  | Contains all order items (products, tax, shipping)  |
| fulfillments  | Array     | Optional  | Contains all in and out shipments                   |
| addresses     | Array     | Optional  | Contains all the customer addresses                 |
| custom        | Array     | Optional  | Custom key/value pairs                              |
| live          | Boolean   | Automatic | True for live mode, false for test mode             |
| created       | Date      | Automatic | Date record was created (in ISO8601 format)         |
| updated       | Date      | Automatic | Date record was updated (in ISO8601 format)         |
| companyId     | String    | Automatic | Your company ID                                     |

## Get Order by ID

> Returns (JSON):

```json
{
  "_id": "5a692f658f6d524e8282dac7",
  "code": "12345",
  "parentCode": "54321",
  "posted": true,
  "shipped": true,
  "billed": true,
  "complete": true,
  "partner": "my-partner",
  "date": "2018-01-28 16:46:13",
  "items": [
    {
      "title": "Great Custom Product",
      "quantity": 2,
      "price": 9.99,
      "sku": "123GRPRODUCT",
      "vendor": "convictional-wholesale",
      "properties": [
        {
          "type": "custom_engraving",
          "data": "We Love Dad!"
        }
      ],
      "grams": 200
    },
    {
      "title": "Great Standard Product",
      "quantity": 1,
      "price": 19.99,
      "sku": "35GRPRODUCT",
      "vendor": "convictional-wholesale",
      "properties": [],
      "grams": 200
    }
  ],
  "fulfillments": [],
  "addresses": [
    {
      "type": "shipping",
      "name": "First Last",
      "company": "Company, Inc",
      "phone": "800-555-5555",
      "city": "Toronto",
      "zip": "M5V 4B3",
      "state": "Ontario",
      "country": "Canada",
      "addressOne": "123 Toronto St.",
      "addressTwo": "#206"
    },
    {
      "type": "billing",
      "name": "First Last",
      "company": "Company, Inc",
      "phone": "800-555-5555",
      "city": "Toronto",
      "zip": "M5V 4B3",
      "state": "Ontario",
      "country": "Canada",
      "addressOne": "123 Toronto St.",
      "addressTwo": "#206"
    }
  ],
  "created": "2018-02-12T15:14:27.147-0500",
  "updated": "2018-02-12T15:14:27.147-0500",
  "companyId": "convictional-wholesale"
}
```

This endpoint returns a single order by ID.

### Endpoint

`https://api.convictional.com/orders/:id`

### Request example

`GET https://api.convictional.com/orders/5a692f658f6d524e8282dac7`

## Get Orders by Query

> Returns (JSON):

```json
[
  {
    "_id": "5a692f658f6d524e8282dac7",
    "code": "12345",
    "parentCode": "54321",
    "posted": true,
    "shipped": true,
    "billed": true,
    "complete": true,
    "partner": "convictional-dropshipper-us",
    "date": "2018-01-28 16:46:13",
    "items": [
      {
        "title": "Great Custom Product",
        "quantity": 2,
        "price": 9.99,
        "sku": "123GRPRODUCT",
        "vendor": "convictional-wholesale",
        "properties": [
          {
            "type": "custom_engraving",
            "data": "We Love Dad!"
          }
        ],
        "grams": 200
      },
      {
        "title": "Great Standard Product",
        "quantity": 1,
        "price": 19.99,
        "sku": "35GRPRODUCT",
        "vendor": "convictional-wholesale",
        "properties": [],
        "grams": 200
      }
    ],
    "fulfillments": [
      {
        "status": "complete",
        "carrier": "USPS",
        "trackingNumbers": [
          "123ABC", "DEF321"
        ],
        "urls": [
          "https://track.com/123ABC",
          "https://track.com/DEF321"
        ],
        "items": [{
          "sku": "123",
          "title": "Product",
          "quantity": 2
        }]
      }
    ],
    "addresses": [
      {
        "type": "shipping",
        "name": "First Last",
        "company": "Company, Inc",
        "phone": "800-555-5555",
        "city": "Toronto",
        "zip": "M5V 4B3",
        "state": "Ontario",
        "country": "Canada",
        "addressOne": "123 Toronto St.",
        "addressTwo": "#206"
      },
      {
        "type": "billing",
        "name": "First Last",
        "company": "Company, Inc",
        "phone": "800-555-5555",
        "city": "Toronto",
        "zip": "M5V 4B3",
        "state": "Ontario",
        "country": "Canada",
        "addressOne": "123 Toronto St.",
        "addressTwo": "#206"
      }
    ],
    "created": "2018-02-12T15:14:27.147-0500",
    "updated": "2018-02-12T15:14:27.147-0500",
    "companyId": "convictional-wholesale"
  },
  {
    "_id": "5a692f658f6d524e8282dac8",
    "code": "12346",
    "parentCode": "54321",
    "posted": true,
    "shipped": true,
    "billed": true,
    "complete": true,
    "partner": "convictional-dropshipper-ca",
    "date": "2018-01-31 13:23:13",
    "items": [
      {
        "title": "Great Custom Product",
        "quantity": 2,
        "price": 9.99,
        "sku": "123GRPRODUCT",
        "vendor": "convictional-wholesale",
        "properties": [
          {
            "type": "custom_engraving",
            "data": "We Love Dad!"
          }
        ],
        "grams": 200
      },
      {
        "title": "Great Standard Product",
        "quantity": 1,
        "price": 19.99,
        "sku": "35GRPRODUCT",
        "vendor": "convictional-wholesale",
        "properties": [],
        "grams": 200
      }
    ],
    "fulfillments": [
      {
        "status": "complete",
        "carrier": "USPS",
        "trackingNumbers": [
          "123ABC", "DEF321"
        ],
        "urls": [
          "https://track.com/123ABC",
          "https://track.com/DEF321"
        ],
        "items": [{
          "sku": "123",
          "title": "Product",
          "quantity": 2
        }]
      }
    ],
    "addresses": [
      {
        "type": "shipping",
        "name": "First Last",
        "company": "Company, Inc",
        "phone": "800-555-5555",
        "city": "Toronto",
        "zip": "M5V 4B3",
        "state": "Ontario",
        "country": "Canada",
        "addressOne": "123 Toronto St.",
        "addressTwo": "#206"
      },
      {
        "type": "billing",
        "name": "First Last",
        "company": "Company, Inc",
        "phone": "800-555-5555",
        "city": "Toronto",
        "zip": "M5V 4B3",
        "state": "Ontario",
        "country": "Canada",
        "addressOne": "123 Toronto St.",
        "addressTwo": "#206"
      }
    ],
    "created": "2018-02-12T15:14:27.147-0500",
    "updated": "2018-02-12T15:14:27.147-0500",
    "companyId": "convictional-wholesale"
  }
]
```

This endpoint returns all your orders.

### Endpoint

`https://api.convictional.com/orders`

### Open example

`GET https://api.convictional.com/orders`

### Filtered example

`GET https://api.convictional.com/orders?createdBefore=2018-02-28T11:26:43.000-0500`

### Query Parameters

| Property      | Type      | Required  | Description                                       |
| ------------  | --------- | ----------| --------------------------------------------------|
| fields        | String    | Optional  | Return only the specified fields, comma separated |
| page          | Number    | Optional  | Return only records on a specific page            |
| limit         | Number    | Optional  | Return up to this number of records               |
| count         | Boolean   | Optional  | Return a count of documents, defaults to false    |
| posted        | Boolean   | Optional  | Filter records by whether they are in your system |
| shipped       | Boolean   | Optional  | Filter records by whether they are shipped        |
| billed        | Boolean   | Optional  | Filter records by whether they are billed         |
| complete      | Boolean   | Optional  | Filter records by whether they are complete       |
| partner       | String    | Optional  | Filter records by a particular partner            |
| code          | String    | Optional  | Filter records by a particular order code         |
| createdBefore | Date      | Optional  | Filter records created before this date (ISO8601) |
| createdAfter  | Date      | Optional  | Filter records created after this date (ISO8601)  |
| updatedBefore | Date      | Optional  | Filter records updated before this date (ISO8601) |
| updatedAfter  | Date      | Optional  | Filter records updated after this date (ISO8601)  |

## Create Order

> Request Body (JSON):

```json
{
  "code": "12345",
  "parentCode": "54321",
  "partner": "convictional-dropshipper-us",
  "date": "2018-01-28 16:46:13",
  "items": [
    {
      "title": "Great Custom Product",
      "quantity": 2,
      "price": 9.99,
      "sku": "123GRPRODUCT",
      "vendor": "convictional-wholesale",
      "properties": [
        {
          "type": "custom_engraving",
          "data": "We Love Dad!"
        }
      ],
      "grams": 200
    },
    {
      "title": "Great Standard Product",
      "quantity": 1,
      "price": 19.99,
      "sku": "35GRPRODUCT",
      "vendor": "convictional-wholesale",
      "properties": [],
      "grams": 200
    }
  ],
  "addresses": [
    {
      "type": "shipping",
      "name": "First Last",
      "company": "Company, Inc",
      "phone": "800-555-5555",
      "city": "Toronto",
      "zip": "M5V 4B3",
      "state": "Ontario",
      "country": "Canada",
      "addressOne": "123 Toronto St.",
      "addressTwo": "#206"
    },
    {
      "type": "billing",
      "name": "First Last",
      "company": "Company, Inc",
      "phone": "800-555-5555",
      "city": "Toronto",
      "zip": "M5V 4B3",
      "state": "Ontario",
      "country": "Canada",
      "addressOne": "123 Toronto St.",
      "addressTwo": "#206"
    }
  ]
}
```

> Returns (JSON):

```json
{
  "_id": "5a692f658f6d524e8282dac7",
  "code": "12345",
  "parentCode": "54321",
  "posted": true,
  "shipped": true,
  "billed": true,
  "complete": true,
  "partner": "convictional-dropshipper-us",
  "date": "2018-01-28 16:46:13",
  "items": [
    {
      "title": "Great Custom Product",
      "quantity": 2,
      "price": 9.99,
      "sku": "123GRPRODUCT",
      "vendor": "convictional-wholesale",
      "properties": [
        {
          "type": "custom_engraving",
          "data": "We Love Dad!"
        }
      ],
      "grams": 200
    },
    {
      "title": "Great Standard Product",
      "quantity": 1,
      "price": 19.99,
      "sku": "35GRPRODUCT",
      "vendor": "convictional-wholesale",
      "properties": [],
      "grams": 200
    }
  ],
  "fulfillments": [
    {
      "status": "complete",
      "carrier": "USPS",
      "trackingNumbers": [
        "123ABC", "DEF321"
      ],
      "urls": [
        "https://track.com/123ABC",
        "https://track.com/DEF321"
      ],
      "items": [{
        "sku": "123",
        "title": "Product",
        "quantity": 2
      }]
    }
  ],
  "addresses": [
    {
      "type": "shipping",
      "name": "First Last",
      "company": "Company, Inc",
      "phone": "800-555-5555",
      "city": "Toronto",
      "zip": "M5V 4B3",
      "state": "Ontario",
      "country": "Canada",
      "addressOne": "123 Toronto St.",
      "addressTwo": "#206"
    },
    {
      "type": "billing",
      "name": "First Last",
      "company": "Company, Inc",
      "phone": "800-555-5555",
      "city": "Toronto",
      "zip": "M5V 4B3",
      "state": "Ontario",
      "country": "Canada",
      "addressOne": "123 Toronto St.",
      "addressTwo": "#206"
    }
  ],
  "created": "2018-02-12T15:14:27.147-0500",
  "updated": "2018-02-12T15:14:27.147-0500",
  "companyId": "convictional-wholesale"
}
```

This endpoint creates a new order.

### Endpoint

`https://api.convictional.com/orders`

### Request example

`POST https://api.convictional.com/orders`

## Update Order

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
  "parentCode": "54321",
  "posted": true,
  "shipped": true,
  "billed": true,
  "complete": true,
  "partner": "convictional-dropshipper-us",
  "date": "2018-01-28 16:46:13",
  "items": [
    {
      "title": "Great Custom Product",
      "quantity": 2,
      "price": 9.99,
      "sku": "123GRPRODUCT",
      "vendor": "convictional-wholesale",
      "properties": [
        {
          "type": "custom_engraving",
          "data": "We Love Dad!"
        }
      ],
      "grams": 200
    },
    {
      "title": "Great Standard Product",
      "quantity": 1,
      "price": 19.99,
      "sku": "35GRPRODUCT",
      "vendor": "convictional-wholesale",
      "properties": [],
      "grams": 200
    }
  ],
  "fulfillments": [
    {
      "status": "complete",
      "carrier": "USPS",
      "trackingNumbers": [
        "123ABC", "DEF321"
      ],
      "urls": [
        "https://track.com/123ABC",
        "https://track.com/DEF321"
      ],
      "items": [{
        "sku": "123",
        "title": "Product",
        "quantity": 2
      }]
    }
  ],
  "addresses": [
    {
      "type": "shipping",
      "name": "First Last",
      "company": "Company, Inc",
      "phone": "800-555-5555",
      "city": "Toronto",
      "zip": "M5V 4B3",
      "state": "Ontario",
      "country": "Canada",
      "addressOne": "123 Toronto St.",
      "addressTwo": "#206"
    },
    {
      "type": "billing",
      "name": "First Last",
      "company": "Company, Inc",
      "phone": "800-555-5555",
      "city": "Toronto",
      "zip": "M5V 4B3",
      "state": "Ontario",
      "country": "Canada",
      "addressOne": "123 Toronto St.",
      "addressTwo": "#206"
    }
  ],
  "created": "2018-02-12T15:14:27.147-0500",
  "updated": "2018-02-12T15:14:27.147-0500",
  "companyId": "convictional-wholesale"
}
```

This endpoint updates a single order by ID.

### Endpoint

`https://api.convictional.com/orders/:id`

### Request example

`PUT https://api.convictional.com/orders/5a692f658f6d524e8282dac7`

## Bulk Update/Create

> Request Body (JSON):

```json
{
  "orders": [
    {
      "code": "12345",
      "parentCode": "54321",
      "posted": true,
      "shipped": true,
      "billed": true,
      "complete": true,
      "partner": "convictional-dropshipper-us",
      "date": "2018-01-28 16:46:13",
      "items": [
        {
          "title": "Great Custom Product",
          "quantity": 2,
          "price": 9.99,
          "sku": "123GRPRODUCT",
          "vendor": "convictional-wholesale",
          "properties": [
            {
              "type": "custom_engraving",
              "data": "We Love Dad!"
            }
          ],
          "grams": 200
        },
        {
          "title": "Great Standard Product",
          "quantity": 1,
          "price": 19.99,
          "sku": "35GRPRODUCT",
          "vendor": "convictional-wholesale",
          "properties": [],
          "grams": 200
        }
      ],
      "addresses": [
        {
          "type": "shipping",
          "name": "First Last",
          "company": "Company, Inc",
          "phone": "800-555-5555",
          "city": "Toronto",
          "zip": "M5V 4B3",
          "state": "Ontario",
          "country": "Canada",
          "addressOne": "123 Toronto St.",
          "addressTwo": "#206"
        },
        {
          "type": "billing",
          "name": "First Last",
          "company": "Company, Inc",
          "phone": "800-555-5555",
          "city": "Toronto",
          "zip": "M5V 4B3",
          "state": "Ontario",
          "country": "Canada",
          "addressOne": "123 Toronto St.",
          "addressTwo": "#206"
        }
      ]
    },
    {
      "code": "12346",
      "parentCode": "54321",
      "posted": true,
      "shipped": true,
      "billed": true,
      "complete": true,
      "partner": "convictional-dropshipper-ca",
      "date": "2018-01-31 13:23:13",
      "items": [
        {
          "title": "Great Custom Product",
          "quantity": 2,
          "price": 9.99,
          "sku": "123GRPRODUCT",
          "vendor": "convictional-wholesale",
          "properties": [
            {
              "type": "custom_engraving",
              "data": "We Love Dad!"
            }
          ],
          "grams": 200
        },
        {
          "title": "Great Standard Product",
          "quantity": 1,
          "price": 19.99,
          "sku": "35GRPRODUCT",
          "vendor": "convictional-wholesale",
          "properties": [],
          "grams": 200
        }
      ],
      "addresses": [
        {
          "type": "shipping",
          "name": "First Last",
          "company": "Company, Inc",
          "phone": "800-555-5555",
          "city": "Toronto",
          "zip": "M5V 4B3",
          "state": "Ontario",
          "country": "Canada",
          "addressOne": "123 Toronto St.",
          "addressTwo": "#206"
        },
        {
          "type": "billing",
          "name": "First Last",
          "company": "Company, Inc",
          "phone": "800-555-5555",
          "city": "Toronto",
          "zip": "M5V 4B3",
          "state": "Ontario",
          "country": "Canada",
          "addressOne": "123 Toronto St.",
          "addressTwo": "#206"
        }
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

This endpoint updates (or creates) orders. If the code matches an existing record, it will update. Otherwise, it will create.

### Endpoint

`https://api.convictional.com/orders`

### Request example

`PUT https://api.convictional.com/orders`

## Delete Order

> Returns (JSON):

```json
{
  "Deleted": 1
}
```

This endpoint deletes a single order by ID.

### Endpoint

`https://api.convictional.com/orders/:id`

### Request example

`DELETE https://api.convictional.com/orders/5a692f658f6d524e8282dac7`