# Orders
REST endpoints that allow you to create, retrieve, update and delete orders.

## Order Properties
| Property      | Type      | Required  | Description                                         |
| -----------   | ------    | --------- | --------------------------------------------------- |
| \_id          | String    | Automatic <td style="width:100%;"> ID of this record        </td>
| code          | String    | Required  | Order number in the source ecommerce system         |
| billed        | Boolean   | Automatic | Has this order been invoiced?                       |
| complete      | Boolean   | Automatic | Is this order shipped and billed?                   |
| posted        | Boolean   | Automatic | Has this order been synced with your system?        |
| partner       | String    | Required  | The partner code that sent this order               |
| date          | String    | Required  | The date of the order (YY/MM/DD hh:mm:ss)           |
| items         | Array     | Required  | Contains all order items (products, tax, shipping)  |
| fulfillments  | Array     | Optional  | Contains all the tracking information               |
| addresses     | Array     | Optional  | Contains all the customer addresses                 |
| returns       | Array     | Optional  | Contains all the returns for this order             |
| created       | Date      | Automatic | Date record was created (in ISO8601 format)         |
| updated       | Date      | Automatic | Date record was updated (in ISO8601 format)         |
| companyId     | String    | Automatic | Your company ID                                     |

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
  "returns": [],
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

## GET - Orders (bulk)

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
    "returns": [],
    "created": "2018-02-12T15:14:27.147-0500",
    "updated": "2018-02-12T15:14:27.147-0500",
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
    "returns": [],
    "created": "2018-02-12T15:14:27.147-0500",
    "updated": "2018-02-12T15:14:27.147-0500",
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
  "billed": false,
  "complete": false,
  "posted": false,
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
  "returns": [],
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

## POST - Orders (bulk)

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
      "billed": true,
      "complete": false,
      "posted": false,
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

>  Returns (JSON):

```json
{
  "0": "5a8755c66affcc608657ed2c",
  "1": "5a8755c66affcc608657ed2d"
}
```
This endpoint creates multiple new orders. Occurs automatically when you pass an array of order objects to this endpoint. 

### Endpoint
`https://api.convictional.com/orders`

### Request Example
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
  "returns": [],
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

## PUT - Orders (bulk)

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
      "billed": true,
      "complete": false,
      "posted": false,
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

## DELETE - Order

> Returns (JSON):

```json
OK
```
This endpoint deletes a single order by ID.

### Endpoint
`https://api.convictional.com/orders/:id`

### Request example
`DELETE https://api.convictional.com/orders/5a692f658f6d524e8282dac7`

## DELETE - Orders (bulk)

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
This endpoint deletes multiple orders by ID.

### Endpoint
`https://api.convictional.com/orders`

### Request Example
`DELETE https://api.convictional.com/orders`