# Partners
The partners endpoints are REST endpoints that allow you to create, retrieve, update and delete partners.

## Partner Properties
Property | Type | Description | Required Field
----------- | ----------- |  -----------  |  -----------
\_id | String | ID of this record in Convictional | Automatic
code | String | The partner code in your system of record | Required
email | String | The main contact email for this partner | Required
active | Boolean | Do you want to sync with this partner? | Required
invited | Boolean | Have they been invited? | Automatic
itemLookup | Array | A reference of your item codes and theirs | Optional
priceList | String | The name of their price list | Optional
relationship | String | Your relationship. 'parent', 'child' or 'self' | Optional
companyId | String | Your company ID in Convictional | Automatic

## GET - Partner

> Returns (JSON):

```json
{
  "_id": "5a692f658f6d524e8282dac7",
  "code": "12345",
  "active": true,
  "email": "capartner@example.com",
  "invited": true,
  "itemLookup": [],
  "priceList": "Price List for Canada",
  "relationship": "child",
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
    "itemLookup": [],
    "priceList": "Price List for Canada",
    "relationship": "child",
    "companyId": "convictional-wholesale"
  },
  {
    "_id": "5a692f658f6d524e8282dac7",
    "code": "12346",
    "active": false,
    "email": "uspartner@example.com",
    "invited": true,
    "itemLookup": [],
    "priceList": "Price List for USA",
    "relationship": "child",
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
  "active": true,
  "email": "capartner@example.com",
  "invited": true,
  "itemLookup": [],
  "priceList": "Price List for Canada",
  "relationship": "child",
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
  "itemLookup": [],
  "priceList": "Price List for Canada",
  "relationship": "child",
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
  "itemLookup": [],
  "priceList": "Price List for Canada",
  "relationship": "child",
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
      "active": true,
      "email": "capartner@example.com",
      "invited": true,
      "itemLookup": [],
      "priceList": "Price List for Canada",
      "relationship": "child",
    },
    {
      "code": "12346",
      "active": false,
      "email": "uspartner@example.com",
      "invited": true,
      "itemLookup": [],
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
    "itemLookup": [],
    "priceList": "Price List for Canada",
    "relationship": "child",
    "companyId": "convictional-wholesale"
  },
  {
    "_id": "5a692f658f6d524e8282dac7",
    "code": "12346",
    "active": false,
    "email": "uspartner@example.com",
    "invited": true,
    "itemLookup": [],
    "priceList": "Price List for USA",
    "relationship": "child",
    "companyId": "convictional-wholesale"
  }
]
```

### Endpoint
`https://api.convictional.com/partners`

### Request example
`PUT https://api.convictional.com/partners`

## DELETE - Partner

> Returns (JSON):

```json
{
  "5a692f658f6d524e8282dac7"
}
```
This endpoint deletes a single partner by ID.

### Endpoint
`https://api.convictional.com/partners/:id`

### Request example
`DELETE https://api.convictional.com/partners/5a692f658f6d524e8282dac7`