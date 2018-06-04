# Products

REST endpoints that allow you to create, retrieve, update and delete products.

## Product Properties

| Property    | Type    | Required    | Description                                   |
| ----------- | ------- | ----------- | --------------------------------------------  |
| \_id        | String  | Automatic   <td style="width:100%;"> ID of this record </td>
| code        | String  | Required    | The product code in your system               |
| title       | String  | Required    | The name of the product                       |
| active      | Boolean | Required    | Is this product active?                       |
| bodyHtml    | String  | Optional    | HTML for consuming-facing pages               |
| images      | Array   | Optional    | Contains image source URLs                    |
| tags        | Array   | Optional    | Contains tags ie. ['summer', 'beauty']        |
| type        | String  | Required    | 'item', 'shipping', 'tax' or 'custom'         |
| variants    | Array   | Required    | All the variations of the product             |
| vendor      | String  | Optional    | The brand of the product                      |
| custom      | Array   | Optional    | Custom key/value pairs                        |
| live        | Boolean | Automatic   | True for live mode, false for test mode       |
| created     | Date    | Automatic   | Date record was created (in ISO8601 format)   |
| updated     | Date    | Automatic   | Date record was updated (in ISO8601 format)   |
| companyId   | String  | Automatic   | Your company ID                               |

## Get Product by ID

> Returns (JSON):

```json
{
  "_id": "5a692f658f6d524e8282dac7",
  "code": "12345",
  "active": true,
  "bodyHtml": "<p>Great product!</p>",
  "images": [
    { "src": "https://cdn.convictional.com/123abc" },
    { "src": "https://cdn.convictional.com/987zyx" },
  ],
  "tags": ["Toronto", "Beauty", "Mens"],
  "title": "Great product",
  "type": "item",
  "variants": [
    { 
      "sku": "123", 
      "title": "Great variant", 
      "inventory_quantity": "8", 
      "price": 9.99 
    },
    { 
      "sku": "321", 
      "title": "Great variant", 
      "inventory_quantity": "3", 
      "price": 19.99 
    }
  ],
  "vendor": "Convictional Wholesale",
  "created": "2018-02-12T15:14:27.147-0500",
  "updated": "2018-02-12T15:14:27.147-0500",
  "live": true,
  "companyId": "convictional-wholesale"
}
```
This endpoint returns a single product by ID.

### Endpoint
`https://api.convictional.com/products/:id`

### Request example
`GET https://api.convictional.com/products/5a692f658f6d524e8282dac7`

## Get Products by Query

> Returns (JSON):

```json
[
  {
    "_id": "5a692f658f6d524e8282dac7",
    "code": "12345",
    "active": true,
    "bodyHtml": "<p>Great product!</p>",
    "images": [
      { "src": "https://cdn.convictional.com/123abc" },
      { "src": "https://cdn.convictional.com/987zyx" },
    ],
    "tags": ["Toronto", "Beauty", "Mens"],
    "title": "Great product",
    "type": "item",
    "variants": [
      { 
        "sku": "123", 
        "title": "Great variant", 
        "inventory_quantity": "8", 
        "price": 9.99 
      },
      { 
        "sku": "321", 
        "title": "Great variant", 
        "inventory_quantity": "3", 
        "price": 19.99 
      }
    ],
    "vendor": "Convictional Wholesale",
    "created": "2018-02-12T15:14:27.147-0500",
    "updated": "2018-02-12T15:14:27.147-0500",
    "live": true,
    "companyId": "convictional-wholesale"
  },
  {
    "_id": "5a692f658f6d524e8282dac8",
    "code": "12346",
    "active": true,
    "bodyHtml": "<p>Greatest product!</p>",
    "images": [
      { "src": "https://cdn.convictional.com/456bec" },
      { "src": "https://cdn.convictional.com/111qwe" },
    ],
    "tags": ["Waterloo", "Fashion", "Womens"],
    "title": "Greatest product",
    "type": "item",
    "variants": [
      { 
        "sku": "456", 
        "title": "Great variant", 
        "inventory_quantity": "12", 
        "price": 29.99 
      },
      { 
        "sku": "789", 
        "title": "Great variant", 
        "inventory_quantity": "6", 
        "price": 39.99 
      }
    ],
    "vendor": "Convictional Wholesale",
    "created": "2018-02-12T15:14:27.147-0500",
    "updated": "2018-02-12T15:14:27.147-0500",
    "live": true,
    "companyId": "convictional-wholesale"
  }
]
```

This endpoint returns all your products.

### Endpoint

`https://api.convictional.com/products`

### Open example

`GET https://api.convictional.com/products`

### Filtered example

`GET https://api.convictional.com/products?createdBefore=2018-02-28T11:26:43.000-0500`

### Query Parameters

| Property      | Type      | Required  | Description                                       |
| ------------  | --------- | ----------| --------------------------------------------------|
| fields        | String    | Optional  | Return only the specified fields, comma separated |
| page          | Number    | Optional  | Return only records on a specific page            |
| limit         | Number    | Optional  | Return up to this number of records               |
| count         | Boolean   | Optional  | Return a count of documents, defaults to false    |
| createdBefore | Date      | Optional  | Filter records created before this date (ISO8601) |
| createdAfter  | Date      | Optional  | Filter records created after this date (ISO8601)  |
| updatedBefore | Date      | Optional  | Filter records updated before this date (ISO8601) |
| updatedAfter  | Date      | Optional  | Filter records updated after this date (ISO8601)  |

## Create Product

> Request Body (JSON):

```json
{
  "code": "12345",
  "active": true,
  "bodyHtml": "<p>Great product!</p>",
  "images": [
    { "src": "https://cdn.convictional.com/123abc" },
    { "src": "https://cdn.convictional.com/987zyx" },
  ],
  "tags": ["Toronto", "Beauty", "Mens"],
  "title": "Great product",
  "type": "item",
  "variants": [
    { 
      "sku": "123", 
      "title": "Great variant", 
      "inventory_quantity": "8", 
      "price": 9.99 
    },
    { 
      "sku": "321", 
      "title": "Great variant", 
      "inventory_quantity": "3", 
      "price": 19.99 
    }
  ],
  "live": true,
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
  "images": [
    { "src": "https://cdn.convictional.com/123abc" },
    { "src": "https://cdn.convictional.com/987zyx" },
  ],
  "tags": ["Toronto", "Beauty", "Mens"],
  "title": "Great product",
  "type": "item",
  "variants": [
    { 
      "sku": "123", 
      "title": "Great variant", 
      "inventory_quantity": "8", 
      "price": 9.99 
    },
    { 
      "sku": "321", 
      "title": "Great variant", 
      "inventory_quantity": "3", 
      "price": 19.99 
    }
  ],
  "vendor": "Convictional Wholesale",
  "created": "2018-02-12T15:14:27.147-0500",
  "updated": "2018-02-12T15:14:27.147-0500",
  "live": true,
  "companyId": "convictional-wholesale"
}
```

This endpoint creates a new product.

### Endpoint

`https://api.convictional.com/products`

### Request example

`POST https://api.convictional.com/products`

## Update Product

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
  "images": [
    { "src": "https://cdn.convictional.com/123abc" },
    { "src": "https://cdn.convictional.com/987zyx" },
  ],
  "tags": ["Toronto", "Beauty", "Mens"],
  "title": "Greater product",
  "type": "item",
  "variants": [
    { 
      "sku": "123", 
      "title": "Great variant", 
      "inventory_quantity": "8", 
      "price": 9.99 
    },
    { 
      "sku": "321", 
      "title": "Great variant", 
      "inventory_quantity": "3", 
      "price": 19.99 
    }
  ],
  "vendor": "Convictional Wholesale",
  "created": "2018-02-12T15:14:27.147-0500",
  "updated": "2018-02-12T15:14:27.147-0500",
  "live": true,
  "companyId": "convictional-wholesale"
}
```

This endpoint updates a single product by ID.

### Endpoint

`https://api.convictional.com/products/:id`

### Request example

`PUT https://api.convictional.com/products/5a692f658f6d524e8282dac7`

## Bulk Update/Create

> Request Body (JSON):

```json
{
  "products": [
    {
      "code": "12345",
      "active": true,
      "bodyHtml": "<p>Great product!</p>",
      "images": [
        { "src": "https://cdn.convictional.com/123abc" },
        { "src": "https://cdn.convictional.com/987zyx" },
      ],
      "tags": ["Toronto", "Beauty", "Mens"],
      "title": "Great product",
      "type": "item",
      "variants": [
        { 
          "sku": "123", 
          "title": "Great variant", 
          "inventory_quantity": "8", 
          "price": 9.99 
        },
        { 
          "sku": "321", 
          "title": "Great variant", 
          "inventory_quantity": "3", 
          "price": 19.99 
        }
      ],
      "vendor": "Convictional Wholesale",
      "live": true
    },
    {
      "code": "12346",
      "active": true,
      "bodyHtml": "<p>Greatest product!</p>",
      "images": [
        { "src": "https://cdn.convictional.com/456bec" },
        { "src": "https://cdn.convictional.com/111qwe" },
      ],
      "tags": ["Waterloo", "Fashion", "Womens"],
      "title": "Greatest product",
      "type": "item",
      "variants": [
        { 
          "sku": "456", 
          "title": "Great variant", 
          "inventory_quantity": "12", 
          "price": 29.99 
        },
        { 
          "sku": "789", 
          "title": "Great variant", 
          "inventory_quantity": "6", 
          "price": 39.99 
        }
      ],
      "vendor": "Convictional Wholesale",
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

This endpoint updates (or creates) products. If the code matches an existing record, it will update. Otherwise, it will create.

### Endpoint

`https://api.convictional.com/products`

### Request example

`PUT https://api.convictional.com/products`

## Delete Product

> Returns (String):

```json
{
  "Deleted": 1
}
```
This endpoint deletes a single product by ID.

### Endpoint

`https://api.convictional.com/products/:id`

### Request example

`DELETE https://api.convictional.com/products/5a692f658f6d524e8282dac7`