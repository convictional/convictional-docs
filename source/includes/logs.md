# Logs
The logs endpoints are REST endpoints that allow you to create, retrieve, update and delete logs.

## Log Properties
Property | Type | Description | Required Field
----------- | ----------- |  -----------  |  -----------
\_id | String | ID of this record in Convictional | Automatic
createDate | String | The date of the log (YY/MM/DD hh:mm:ss) | Automatic
description | String | A description of what happened | Required
companyId | String | Your company ID in Convictional | Automatic

## GET - Log

> Returns (JSON):

```json
{
  "_id": "5a692f658f6d524e8282dac7",
  "createDate": "01/24/18 20:13:05",
  "description": "Welcome to Convictional, convictional-wholesale",
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
    "createDate": "01/24/18 20:13:05",
    "description": "Welcome to Convictional, convictional-wholesale",
    "companyId": "convictional-wholesale"
  },
  {
    "_id": "5a692f658f6d524e8282dac8",
    "createDate": "01/24/18 20:13:06",
    "description": "Successfully created partner from: convictional-wholesale",
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
  "description": "Welcome to Convictional, convictional-wholesale"
}
```

> Returns (JSON):

```json
{
  "_id": "5a692f658f6d524e8282dac7",
  "createDate": "01/24/18 20:13:05",
  "description": "Welcome to Convictional, convictional-wholesale",
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
  "createDate": "01/24/18 20:13:05",
  "description": "Welcome to Convictional!",
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
      "description": "Welcome to Convictional, convictional-wholesale"
    },
    {
      "description": "Successfully created partner from: convictional-wholesale"
    }
  ]
}
```

> Returns (JSON):

```json
[
  {
    "_id": "5a692f658f6d524e8282dac7",
    "createDate": "01/24/18 20:13:05",
    "description": "Welcome to Convictional, convictional-wholesale",
    "companyId": "convictional-wholesale"
  },
  {
    "_id": "5a692f658f6d524e8282dac8",
    "createDate": "01/24/18 20:13:06",
    "description": "Successfully created partner from: convictional-wholesale",
    "companyId": "convictional-wholesale"
  }
]
```


### Endpoint
`https://api.convictional.com/logs`

### Request example
`PUT https://api.convictional.com/logs`

## DELETE - Log

> Returns (JSON):

```json
{
  "5a692f658f6d524e8282dac7"
}
```
This endpoint deletes a single log by ID.

### Endpoint
`https://api.convictional.com/logs/:id`

### Request example
`DELETE https://api.convictional.com/logs/5a692f658f6d524e8282dac7`