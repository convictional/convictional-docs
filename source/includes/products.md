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
| created     | Date    | Automatic   | Date record was created (in ISO8601 format)   |
| updated     | Date    | Automatic   | Date record was updated (in ISO8601 format)   |
| companyId   | String  | Automatic   | Your company ID                               |

## GET - Product

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
    "companyId": "convictional-wholesale"
  }
]
```
This endpoint updates (or creates) products.

### Endpoint
`https://api.convictional.com/products`

### Request example
`PUT https://api.convictional.com/products`

## DELETE - Product

> Returns (String):

```json
OK
```
This endpoint deletes a single product by ID.

### Endpoint
`https://api.convictional.com/products/:id`

### Request example
`DELETE https://api.convictional.com/products/5a692f658f6d524e8282dac7`