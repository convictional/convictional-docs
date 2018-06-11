# Introduction

> API Endpoint:

```json
https://api.convictional.com
https://api.convictional.com/(resource)/(id)
https://api.convictional.com/(resource)/(query)
https://api.convictional.com/(action)
```

Welcome to the Convictional API. You can use our API to access various resources on the Convictional platform. We use this API (and this document) to build our own applications. 

Our goal providing an API for our service is to allow technically inclined customers to take advantage of the infrastructure, business rules, integrations and admin capabilities of our platform.

## Versioning

> Last Updated:

```json
{
  "2018-06-08"
}
```

When breaking changes happen, we will notify users and migrate you. Our long-term goal is stability: EDI is not something that changes very often and custom fields can be used for anything customer-specific.

## Authentication

> Request Headers:

```json
{ 
  "Authentication": "5ba82897-0bff-4e4e-842e"
}
```

Convictional uses API keys to authenticate your requests. When you register, we generate a key for you. To find your key, login to Convictional and go to "Settings". Include your API key in the "Authorization" header to authenticate your request and access your account. If you need a refresh, contact support.

## Bulk Endpoints

> Request Body (JSON):

```json
[
  {},
  {},
  {},
  ... up to 97 more records.
]
```

Convictional offers bulk create/update and read endpoints. You can create/update up to 100 records at once, and read up to 500. The max request/response size is 6mb. Our client library handles queuing of requests, so we recommend it if you plan to do a lot of bulk requests.

## Client Libraries

> Require Statement:

```javascript
// Top of your file with all your requires:
var convictional = require('convictional')({
  'apiKey': '86e7ccdc-55b5-4066-a79f-7a1e0e59c690'
})
 
// ... later where you want to use it:
var orderId = '5a692f658f6d524e8282dac7'
convictional.getOrder(orderId).then((order) => {
  // Do stuff with this particular order
}).catch((error) => { console.error(error) })

convictional.getOrders({}).then((orders) => {
  // Do stuff with all your orders
}).catch((error) => { console.error(error) })

```

Convictional offers a client library for Node.JS. For more information visit the [libary on NPM](https://npmjs.com/package/convictional).

The client library will validate your request, check to make sure the right data is provided and throw a useful error if not. We use it to write all of our customer-specific applications, so you can trust it will continue to stay up to date with API changes.

It will also handle queueing of bulk requests so you can make one call for an unlimited number (limited by your machine's memory) of records. All endpoints can be accessed through the client library.

## Responses

> 200: Returns (String):

```json
{
  "OK"
}
```

> 400: Returns (String):

```json
{
  "Not found"
}
```

> 401: Returns (String): 

```json
{
  "Not authorized"
}
```

> 500: Returns (String):

```json
{
  "Bad request"
}
```

The Convictional API uses the following response codes:

| Code      | Description     |
| --------- | --------------- |
| 200       <td style="width:100%;">OK: means your request was successful.</td> |
| 307       | Redirect: means this handler wants you to go somewhere else.      |
| 400       | Not found: means the ID or code of the resource cannot be found.  |
| 401       | Not authorized: means the "Authorization" header API kye is wrong.|
| 500       | Bad request: means something about your request body isn't right. |

## Custom Data

> Schema:

```json
{
  "_id": "ObjectID",
  "key": "string",
  "type": "string",
  "value": "string"
}
```

> Example:

```json
[
  {
    "_id": "5425345jh43lkh25jk",
    "key": "api_key",
    "type": "string",
    "value": "123ABC-DEF456"
  },
  {
    "_id": "5425345jh43lkh25jk",
    "key": "status_code",
    "type": "number",
    "value": "123"
  },
  {
    "_id": "5425345jh43lkh25jk",
    "key": "product_data",
    "type": "json",
    "value": "{ code: ABC, quantity: 3 }"
  }
]
```

Convictional allows use of custom key/value pairs on all resources. The three types we currently support are: strings, numbers and arbitrary JSON. All three will be stored as strings but you can convert them into the right type based on what is in the type field when you need to use it.

## Data Types

```json
{
  "string": "string",
  "number": 0,
  "json": { "this_is": "json" },
  "boolean": true,
  "date": "2018-05-31T18:03:24+00:00"
}
```

| Type    | Description |
| ------- | ----------- |
| string  | A string can be any length and contain alphanumberic characters |
| number  | A number can be any size and contain numberic characters        |
| json    | A JSON object can contain arbitrary JSON                        |
| boolean | A boolean is either true or false                               |
| date    | A date in ISO 8601 format ("YYYY-MM-DDThh:mm:ss.sss-hh:mm")     |
