# Logs
REST endpoints that allow you to create, retrieve, update and delete logs.

## Log Properties
| Property    | Type   | Required  | Description                                  |
| ----------- | ------ | --------- | -------------------------------------------- |
| \_id        | String | Automatic <td style="width:100%;"> ID of this record </td>
| description | String | Required  | A description of what you are logging        |
| created     | Date   | Automatic | Date record was created (in ISO8601 format)  |
| updated     | Date   | Automatic | Date record was updated (in ISO8601 format)  |
| companyId   | String | Automatic | Your company ID                              |

## GET - Log

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

## GET - Logs

> Returns (JSON): 

```json
[
  {
    "_id": "5a692f658f6d524e8282dac7",
    "description": "Welcome to Convictional",
    "created": "2018-02-12T15:14:27.147-0500",
    "updated": "2018-02-12T15:14:27.147-0500",
    "companyId": "convictional-wholesale"
  },
  {
    "_id": "5a692f658f6d524e8282dac8",
    "description": "Successful request",
    "created": "2018-02-12T15:14:27.147-0500",
    "updated": "2018-02-12T15:14:27.147-0500",
    "companyId": "convictional-wholesale"
  }
]
```
This endpoint returns all your logs.

### Endpoint
`https://api.convictional.com/logs`

### Request example
`GET https://api.convictional.com/logs`

## POST - Log

> Request Body (JSON):

```json
{
  "description": "Welcome to Convictional"
}
```

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

This endpoint creates a new log.

### Endpoint
`https://api.convictional.com/logs`

### Request example
`POST https://api.convictional.com/logs`

## PUT - Log
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
  "companyId": "convictional-wholesale"
}
```

This endpoint updates a single log by ID.

### Endpoint
`https://api.convictional.com/logs/:id`

### Request example
`PUT https://api.convictional.com/logs/5a692f658f6d524e8282dac7`

## PUT - Logs

> Request Body (JSON):

```json
{
  "logs": [
    {
      "description": "Welcome to Convictional"
    },
    {
      "description": "Successful request"
    }
  ]
}
```

> Returns (JSON):

```json
[
  {
    "_id": "5a692f658f6d524e8282dac7",
    "description": "Welcome to Convictional",
    "created": "2018-02-12T15:14:27.147-0500",
    "updated": "2018-02-12T15:14:27.147-0500",
    "companyId": "convictional-wholesale"
  },
  {
    "_id": "5a692f658f6d524e8282dac8",
    "description": "Successful request",
    "created": "2018-02-12T15:14:27.147-0500",
    "updated": "2018-02-12T15:14:27.147-0500",
    "companyId": "convictional-wholesale"
  }
]
```
This endpoint updates (or creates) logs.

### Endpoint
`https://api.convictional.com/logs`

### Request example
`PUT https://api.convictional.com/logs`

## DELETE - Log

> Returns (JSON):

```json
OK
```
This endpoint deletes a single log by ID.

### Endpoint
`https://api.convictional.com/logs/:id`

### Request example
`DELETE https://api.convictional.com/logs/5a692f658f6d524e8282dac7`