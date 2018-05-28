# Introduction

> API Endpoint:

```json
https://api.convictional.com
```

Welcome to the Convictional API documentation. You can use our API to access various resources on the Convictional platform. We use this API and this documentation every day to build our own applications, so we build it to be as easy to use and scalable as we can.

Our goal providing an API for our service is to allow technically inclined customers to take advantage of the infrastructure, business rules, integrations and admin capabilities of our platform. Almost anything you can do in the admin, you can do here too. Let us know what you think.

## Versioning

> Last Updated:

```json
{ "2018-05-24" }
```

When breaking changes happen in the future, we will notify users and migrate you to the new version. 

## Authentication

> Request Headers:

```json
{ 
  "Authentication": "5ba82897-0bff-4e4e-842e"
}
```

Convictional uses API keys to authenticate your requests. When you register your account, we generate an API key for you. To find your key, login to Convictional and go to "Settings". Include your API key in the "Authorization" header to authenticate your request.

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

Convictional offers bulk endpoints. This allows you to create, read and update up to 100 records as once. You can go above 100 records at a time but your request may be rejected on the basis of size. The max data size is 6mb. If you use our client library we handle the queuing and chunking for you. Send an array of records instead of a single record to create, update and delete endpoints to use bulk abilities.

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
  // Do stuff with record...
}).catch((error) => { console.error(error) })

```

Convictional currenly offers a client library for Node.JS. For more information visit the [client libary on NPM](https://npmjs.com/package/convictional).

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

Convictional allows use of custom key/value pairs on all records. Over time we will migrate some of our more user-specific fields over to use this format, so you can define your own data.

The three types we currently support are: strings, numbers and JSON. All three will be stored as strings but you can convert them into the right type based on what is in the type field.

## Data Types

```json
{
  "string": "string",
  "number": 0,
  "json": { "this_is": "json" },
  "boolean": true
}
```

Convictional supports various data types. The main ones are strings, numbers, json and booleans. 