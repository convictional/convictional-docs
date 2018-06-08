# Logs

REST endpoints that allow you to create, retrieve, update and delete logs.

## Log Properties

| Property    | Type    | Required  | Description                                  |
| ----------- | ------- | --------- | -------------------------------------------- |
| \_id        | String  | Automatic <td style="width:100%;"> ID of this record </td>
| description | String  | Required  | A description of what you are logging        |
| custom      | Array   | Optional  | Custom key/value pairs                       |
| live        | Boolean | Automatic | True for live mode, false for test mode      |
| created     | Date    | Automatic | Date record was created (in ISO8601 format)  |
| updated     | Date    | Automatic | Date record was updated (in ISO8601 format)  |
| companyId   | String  | Automatic | Your company ID                              |

## Get Log by ID

> Returns (JSON):

```json
{
  "_id": "5a692f658f6d524e8282dac7",
  "description": "Welcome to Convictional",
  "created": "2018-02-12T15:14:27.147-0500",
  "updated": "2018-02-12T15:14:27.147-0500",
  "companyId": "convictional-wholesale"
}
```

This endpoint returns a single log by ID.

### Endpoint

`https://api.convictional.com/logs/:id`

### Request example

`GET https://api.convictional.com/logs/5a692f658f6d524e8282dac7`

## Get Logs by Query

> Returns (JSON):

```json
[
  {
    "_id": "5a692f658f6d524e8282dac7",
    "description": "Welcome to Convictional",
    "created": "2018-02-12T15:14:27.147-0500",
    "updated": "2018-02-12T15:14:27.147-0500",
    "custom": [
      {
        "key": "statusCode",
        "type": "number",
        "value": 200
      },
      {
        "key": "path",
        "type": "string",
        "value": "/orders"
      }
    ],
    "live": true,
    "companyId": "convictional-wholesale"
  },
  {
    "_id": "5a692f658f6d524e8282dac8",
    "description": "Successful request",
    "created": "2018-02-12T15:14:27.147-0500",
    "updated": "2018-02-12T15:14:27.147-0500",
    "custom": [
      {
        "key": "statusCode",
        "type": "number",
        "value": 200
      },
      {
        "key": "path",
        "type": "string",
        "value": "/orders"
      }
    ],
    "live": true,
    "companyId": "convictional-wholesale"
  }
]
```

This endpoint returns all your logs.

### Get

`https://api.convictional.com/logs`

### Open example

`GET https://api.convictional.com/logs`

### Filtered example

`GET https://api.convictional.com/logs?createdBefore=2018-02-28T11:26:43.000-0500`

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

## Create Log

> Request Body (JSON):

```json
{
  "description": "Welcome to Convictional",
  "custom": [
      {
        "key": "statusCode",
        "type": "number",
        "value": 200
      },
      {
        "key": "path",
        "type": "string",
        "value": "/orders"
      }
    ],
}
```

> Returns (JSON):

```json
{
  "_id": "5a692f658f6d524e8282dac7",
  "description": "Welcome to Convictional",
  "created": "2018-02-12T15:14:27.147-0500",
  "updated": "2018-02-12T15:14:27.147-0500",
  "custom": [
    {
      "key": "statusCode",
      "type": "number",
      "value": 200
    },
    {
      "key": "path",
      "type": "string",
      "value": "/orders"
    }
  ],
  "live": true,
  "companyId": "convictional-wholesale"
}
```

This endpoint creates a new log.

### Endpoint

`https://api.convictional.com/logs`

### Request example

`POST https://api.convictional.com/logs`

## Update Log

> Request Body (JSON):

```json
{
  "description": "Welcome to Convictional!"
}
```

> Returns (JSON):

```json
{
  "_id": "5a692f658f6d524e8282dac7",
  "description": "Welcome to Convictional!",
  "created": "2018-02-12T15:14:27.147-0500",
  "updated": "2018-02-12T15:14:27.147-0500",
  "custom": [
    {
      "key": "statusCode",
      "type": "number",
      "value": 200
     },
    {
      "key": "path",
      "type": "string",
      "value": "/orders"
    }
  ],
  "live": true,
  "companyId": "convictional-wholesale"
}
```

This endpoint updates a single log by ID.

### Endpoint

`https://api.convictional.com/logs/:id`

### Request example

`PUT https://api.convictional.com/logs/5a692f658f6d524e8282dac7`

## Bulk Update/Create

> Request Body (JSON):

```json
{
  "logs": [
    {
      "_id": "5a692f658f6d524e8282dac7",
      "description": "Welcome to Convictional"
    },
    {
      "_id": "5a692f658f6d524e8282dac7",
      "description": "This is a new description"
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

This endpoint updates (or creates) logs. If the ID matches an existing record, it will update. Otherwise, it will create.

### Endpoint

`https://api.convictional.com/logs`

### Request example

`PUT https://api.convictional.com/logs`

## Delete Log

> Returns (JSON):

```json
{
  "Deleted": 1
}
```

This endpoint deletes a single log by ID.

### Endpoint

`https://api.convictional.com/logs/:id`

### Request example

`DELETE https://api.convictional.com/logs/5a692f658f6d524e8282dac7`