# Introduction

> API Endpoint:

```json
https://api.convictional.com
```

Welcome to the Convictional Commerce API documentation. You can use our API to access various resources on the Convictional platform. We provide various examples on the right, with documentation in the middle and search on the left. We use this API and this documentation every day to build our own applications, so we build it to be as easy to use, stable and scalable as we can.

Our goal providing an API for our service is to allow technically inclined customers to take advantage of the infrastructure, business rules, integrations and admin capabilities of our platform. Almost anything you can do in the admin, you can do here too.

# Versioning

> Last Updated:

```json
2018-01-31
```

Our API is still on the first version. When breaking changes happen in the future, we will notify users and migrate you to the new version. If you have any feedback, please get in touch. We are always open to adding new endpoints to make it as easy as possible for our customers to trade with their partners. 

# Authentication
Convictional uses API keys to authenticate your requests. When you register your account, we generate an API key for you. To find your key, login to Convictional and go to "Settings". Include your API key in the "Authorization" header to authenticate your request.

# Responses

> 200: Returns (String):

```json
OK
```

> 400: Returns (String):

```json
Not found
```

> 401: Returns (String): 

```json
Not authorized
```

> 500: Returns (String):

```json
Bad request
```

The Convictional API uses the following response codes:

| Code      | Description     |
| --------- | --------------- |
| 200       <td style="width:100%;">OK</td> |
| 400       | Not found       |
| 401       | Not authorized  |
| 500       | Bad request     |