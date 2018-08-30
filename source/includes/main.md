# Overview

> API Endpoint:

```http
URL: https://api.convictional.com
```

Welcome to the Convictional API. The purpose of the API is the same as the rest of our products: make it easier to sell to online retailers. Our customers and in-house development team use it.

## Versioning

> Last Updated:

```http
Date: 2018-08-22
```

When breaking changes happen, we will notify users and migrate you. Our long-term goal is stability: B2B is not something that changes very often and custom fields can be used for anything customer-specific.

## Authentication

> Request Headers:

```http
Authentication: 5ba82897-0bff-4e4e-842e
```

Convictional uses API keys to authenticate your requests. To find your key, login to Convictional and go to "Settings". Include your API key in the "Authorization" header to authenticate your requests.

## Other Headers

> Other Headers:

```http
Content-Type: application/json
Accept: application/json
```

We optionally accept Content-Type and Accept headers. We only support JSON, but in certain cases we can also work with text/plain types involving EDI documents. So assume JSON unless specified.

## Rate Limits

The API does not have rate limits at this time. Our client library does queuing for you, or you can queue things yourself. If we change this policy in future, we will notify all our customers in advance.

> Rate Limit Headers:

```http
X-RateLimit-Limit: Unlimited
X-RateLimit-Remaining: Unlimited
X-RateLimit-Reset: Unlimited
```

## Response Types

> 200: GET, POST or PUT Returns (JSON):

```json
{
  "(content)"
}
```

> 200: DELETE Returns (JSON):

```json
{
  "deleted": 1
}
```

> 200: Bulk PUT Returns (JSON):

```json
{
  "updated": 2
}
```

> 400: Returns (JSON):

```json
{
  "error": "not found"
}
```

> 401: Returns (JSON):

```json
{
  "error": "unauthorized"
}
```

> 402+: Returns (JSON):

```json
{
  "error": "(something you did wrong)"
}
```

> 500+: Returns (JSON):

```json
{
  "error": "(something we did wrong)"
}
```

The API uses a variety of status codes to indicates success or failure of a particular request. The 200 series means success, the 400 series means something is wrong on your side, and the 500 series means something is wrong on our side. If you need help, contact support.

## Custom Meta Data

> Schema:

```json
{
  "_id": "string",
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
| number  | A number can be any size and contain numberic characters only   |
| json    | A JSON object can contain arbitrary JSON encoded data           |
| boolean | A boolean is either true or false                               |
| date    | A date in ISO 8601 format ("YYYY-MM-DDThh:mm:ss.sss-hh:mm")     |

The API deals in a variety of data types, always encoded in valid JSON. We support strings, dates, numbers and booleans. A JSON schema is provided for each resource and we will reject any incorrectly typed objects to ensure type safety across systems we connect to.

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

Convictional offers a client library for Node.JS. For more information visit the [libary on NPM](https://npmjs.com/package/convictional). Other languages will be added as needed.

The client library will validate your request, check to make sure the right data is provided to perform a successful request and throw a useful error if not. We use it to write all of our customer-specific applications, so you can trust it will continue to stay up to date with API changes.

It will also handle queueing of bulk requests so you can make one call for an unlimited number (limited by your machine's memory) of records. All endpoints can be accessed through the client library.

## Health & Status

[Click here](https://api.convictional.com) to see the health of the API at any time.

OK means online, anything else means the API is offline.

> Request (HTTP):

```http
GET https://api.convictional.com
```

> Response (HTTP):

```http
Body: OK
Status: 200
```