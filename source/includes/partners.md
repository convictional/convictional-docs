# Partners
REST endpoints that allow you to create, retrieve, update and delete partners.

## Partner Properties
| Property     | Type     | Required  | Description                                 |
| ------------ | ---------| ----------| ------------------------------------------- |
| \_id         | String   | Automatic <td style="width:100%;"> ID of this record </td>
| code         | String   | Required  | The partner code in your system             |
| email        | String   | Required  | The business email for this partner         |
| active       | Boolean  | Required  | Do you want to sync with them?              |
| invited      | Boolean  | Automatic | Have they been invited?                     |
| priceList    | String   | Optional  | The name of their price list                |
| relationship | String   | Required  | Relation to you 'parent', 'child' or 'self' |
| itemLookup   | Array    | Optional  | A reference of your item codes and theirs   |
| created      | Date     | Automatic | Date record was created (in ISO8601 format) |
| updated      | Date     | Automatic | Date record was updated (in ISO8601 format) |
| companyId    | String   | Automatic | Your company ID                             |

## GET - Partner

> Returns (JSON):

```json
{
  "_id": "5a692f658f6d524e8282dac7",
  "code": "12345",
  "active": true,
  "email": "capartner@example.com",
  "invited": true,
  "itemLookup": [
    {
      "myId": "12345",
      "partnerId": "ABC123"
    },
    {
      "myId": "56789",
      "partnerId": "XYZ098"
    }
  ],
  "priceList": "Price List for Canada",
  "relationship": "child",
  "created": "2018-02-12T15:14:27.147-0500",
  "updated": "2018-02-12T15:14:27.147-0500",
  "companyId": "convictional-wholesale"
}
```
This endpoint returns a single partner by ID.

### Endpoint
`https://api.convictional.com/partners/:id`

### Request example
`GET https://api.convictional.com/partners/5a692f658f6d524e8282dac7`

## GET - Partners

> Returns (JSON):

```json
[
  {
    "_id": "5a692f658f6d524e8282dac7",
    "code": "12345",
    "active": true,
    "email": "capartner@example.com",
    "invited": true,
    "itemLookup": [
      {
        "myId": "12345",
        "partnerId": "ABC123"
      },
      {
        "myId": "56789",
        "partnerId": "XYZ098"
      }
    ],
    "priceList": "Price List for Canada",
    "relationship": "child",
    "created": "2018-02-12T15:14:27.147-0500",
    "updated": "2018-02-12T15:14:27.147-0500",
    "companyId": "convictional-wholesale"
  },
  {
    "_id": "5a692f658f6d524e8282dac7",
    "code": "12346",
    "active": false,
    "email": "uspartner@example.com",
    "invited": true,
    "itemLookup": [
      {
        "myId": "12345",
        "partnerId": "ABC123"
      },
      {
        "myId": "56789",
        "partnerId": "XYZ098"
      }
    ],
    "priceList": "Price List for USA",
    "relationship": "child",
    "created": "2018-02-12T15:14:27.147-0500",
    "updated": "2018-02-12T15:14:27.147-0500",
    "companyId": "convictional-wholesale"
  }
]
```
This endpoint returns all your partners.

### Endpoint
`https://api.convictional.com/partners`

### Request example
`GET https://api.convictional.com/partners`

## POST - Partner

> Request Body (JSON):

```json
{
  "code": "12345",
  "email": "capartner@example.com",
  "priceList": "Price List for Canada",
  "relationship": "child"
}
```

> Returns (JSON):

```json
{
  "_id": "5a692f658f6d524e8282dac7",
  "code": "12345",
  "active": true,
  "email": "capartner@example.com",
  "invited": true,
  "itemLookup": [
    {
      "myId": "12345",
      "partnerId": "ABC123"
    },
    {
      "myId": "56789",
      "partnerId": "XYZ098"
    }
  ],
  "priceList": "Price List for Canada",
  "relationship": "child",
  "created": "2018-02-12T15:14:27.147-0500",
  "updated": "2018-02-12T15:14:27.147-0500",
  "companyId": "convictional-wholesale"
}
```
This endpoint creates a new partner.

### Endpoint
`https://api.convictional.com/partners`

### Request example
`POST https://api.convictional.com/partners`

## PUT - Partner

> Request Body (JSON):

```json
{
  "active": false
}
```

> Returns (JSON):

```json
{
  "_id": "5a692f658f6d524e8282dac7",
  "code": "12345",
  "active": false,
  "email": "capartner@example.com",
  "invited": true,
  "itemLookup": [
    {
      "myId": "12345",
      "partnerId": "ABC123"
    },
    {
      "myId": "56789",
      "partnerId": "XYZ098"
    }
  ],
  "priceList": "Price List for Canada",
  "relationship": "child",
  "created": "2018-02-12T15:14:27.147-0500",
  "updated": "2018-02-12T15:14:27.147-0500",
  "companyId": "convictional-wholesale"
}
```
This endpoint updates a single partner by ID.

### Endpoint
`https://api.convictional.com/partners/:id`

### Request example
`PUT https://api.convictional.com/partners/5a692f658f6d524e8282dac7`

## PUT - Partners

> Request Body (JSON):

```json
{
  "partners": [
    {
      "code": "12345",
      "email": "capartner@example.com",
      "priceList": "Price List for Canada",
      "relationship": "child",
    },
    {
      "code": "12346",
      "email": "uspartner@example.com",
      "priceList": "Price List for USA",
      "relationship": "child",
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
    "email": "capartner@example.com",
    "invited": true,
    "itemLookup": [
      {
        "myId": "12345",
        "partnerId": "ABC123"
      },
      {
        "myId": "56789",
        "partnerId": "XYZ098"
      }
    ],
    "priceList": "Price List for Canada",
    "relationship": "child",
    "created": "2018-02-12T15:14:27.147-0500",
    "updated": "2018-02-12T15:14:27.147-0500",
    "companyId": "convictional-wholesale"
  },
  {
    "_id": "5a692f658f6d524e8282dac7",
    "code": "12346",
    "active": false,
    "email": "uspartner@example.com",
    "invited": true,
    "itemLookup": [
      {
        "myId": "12345",
        "partnerId": "ABC123"
      },
      {
        "myId": "56789",
        "partnerId": "XYZ098"
      }
    ],
    "priceList": "Price List for USA",
    "relationship": "child",
    "created": "2018-02-12T15:14:27.147-0500",
    "updated": "2018-02-12T15:14:27.147-0500",
    "companyId": "convictional-wholesale"
  }
]
```
This endpoint updates (or creates) partners.

### Endpoint
`https://api.convictional.com/partners`

### Request example
`PUT https://api.convictional.com/partners`

## DELETE - Partner

> Returns (JSON):

```json
OK
```
This endpoint deletes a single partner by ID.

### Endpoint
`https://api.convictional.com/partners/:id`

### Request example
`DELETE https://api.convictional.com/partners/5a692f658f6d524e8282dac7`

## DELETE - Partners (bulk)

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
This endpoint deletes multiple partners by ID.

### Endpoint
`https://api.convictional.com/partners`

### Request Example
`DELETE https://api.convictional.com/partners`