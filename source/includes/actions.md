# Actions

Action-oriented (RPC) endpoints that allow you to translate EDI documents, transmit files over FTP, invite your trading partners, run sync workers and more.

## Sync

> Returns (JSON):

```json
{
  "Successfully pushed getOrders to queue"
}
```

This endpoint allows you to initiate a sync method of your choosing.

### Sync Endpoint

`https://api.convictional.com/sync/:method`

### Sync Example

`GET https://api.convictional.com/sync/getOrders`

### Sync Methods

| Method            | Description                                                                     |
| ----------------  |-----------------------------------------------------|
| getOrders         | Get the orders from all your trading partners       |
| getOrderUpdates   | Get order updates from your system                  |
| postOrders        | Push orders from Convictional into your system      |
| postOrderUpdates  | Push order updates to all your trading partners     |
| getProducts       | Get products from your system                       |
| postProducts      | Push products to your trading partners              |
| getProductUpdates | Get inventory from your system                      |
| postProductUpdates| Push inventory to your trading partners             |
| postInvoices      | Invoice and charge for shipped orders               |
| getSkuById        | Get SKU ID in attached partner shops                |

## Translate

> Returns (JSON):

```json
{
  "segmentID": {
    "0": "first_element_value",
    "1": "second_element_value",
    "2": "third_element_value"
  },
  "segmentID": [
    {
      "0": "first_element_value",
      "1": "second_element_value",
      "2": "third_element_value"
    },
    {
      "0": "first_element_value",
      "1": "second_element_value",
      "2": "third_element_value"
    }
  ]
}
```

This endpoint allows you to convert an X12 EDI document in raw text into JSON.

### Translate Endpoint

`https://api.convictional.com/translate`

### Translate Example

`POST https://api.convictional.com/translate`

### Translate Properties

| Property | Description                                                                           |
| -------- | ------------------------------------------------------------------------------------- |
| body     <td style="width:100%;"> The request body must contain an X12 EDI document in text </td>

### Query Parameters

| Property      | Type      | Required  | Description                                       |
| ------------  | --------- | ----------| --------------------------------------------------|
| raw           | Boolean   | Optional  | Return raw document (default: true)               |

## Transmit

> Request (JSON):

```json
{
  "fileName": "folder.fileName.txt",
  "document": "This is the contents of the file.",
  "credentials": {
    "host": "127.0.0.1",
    "port": "21",
    "user": "anonymous",
    "pass": "@anonymous"
  }
}
```

> Success Returns (JSON):

```json
{
  "status": "completed"
}
```

> Failure Returns (JSON):

```json
{
  "error": "No document provided."
},
{
  "error": "No file name provided."
},
{
  "error": "No credentials provided."
},
{
  "error": "(other connection errors)"
}
```

This endpoint allows you to send a document via FTP with provided credentials and file name.

### Transmit Endpoint

`https://api.convictional.com/transmit`

### Transmit Example

`POST https://api.convictional.com/transmit`

### Transmit Properties

| Property    | Type      | Required  | Description                                                     |
| ----------- | --------- | ----------| --------------------------------------------------------------- |
| fileName    | string    | Required  | The name of the file. For folders, put 'folder.folder.file.txt' |
| document    | string    | Required  | The contents of the document in plain text. Any format.         |
| credentials | json      | Required  | The credentials of the FTP server you want to send this to.     |

#### Credentials Properties

| Property    | Type      | Required  | Description                                                     |
| ----------- | --------- | ----------| --------------------------------------------------------------- |
| host        | string    | Required  | The hostname or IP address of the FTP server.                   |
| port        | string    | Required  | The port of the FTP server.                                     |
| user        | string    | Required  | Username for authentication.                                    |
| pass        | string    | Required  | Password for authentication.                                    |

## Invite

> Request (JSON):

```json
{
  "email": "test@convictional.com",
  "companyName": "Supplier, Inc.",
  "billing": true
}
```

> Returns (JSON):

```json
{
  "Invited partner: test@convictional.com"
}
```

This endpoint invites a single partner by email.

### Invite Endpoint

`https://api.convictional.com/partners/invite`

### Invite Example

`POST https://api.convictional.com/partners/invite`

### Message example

<p style="background:white;"><br>
<b>Subject:</b> You are invited to trade with: supplier<br><br>
<b>Body:</b><br>
You are invited to trade with: supplier<br><br>

1. Click the link below and make an account.<br>
2. Then go to settings and connect to your store.<br><br>

https://app.convictional.com/sign_up?billing=true&shop=supplier<br><br>
</p>

### Invite Properties

| Property    | Type      | Required  | Description                                              |
| ----------- | --------- | ----------| -------------------------------------------------------- |
| email       | string    | Required  | The email of the partner you want to invite.             |
| companyName | string    | Optional  | Your company name so your partners recognize it.         |
| billing     | boolean   | Optional  | Default: true. Do you want to get a credit card on file? |

## Quick Order

> Request Body (JSON)

```json
{
  "source": "customer@domain.com",
  "subject": "convictional-wholesale",
  "items" : [
    {
      "sku": "ABC123",
      "quantity": 1
    },
    {
      "sku": "DEF456",
      "quantity": 2
    }
  ],
  "address": {
    "name": "First Last",
    "company": "Company, Inc",
    "phone": "4165555555",
    "email": "orders@customer.com",
    "type": "shipping",
    "city": "Toronto",
    "zip": "M5V4B3",
    "state": "Ontario",
    "country": "Canada",
    "address": "123 St.",
    "addressTwo": "#101"
  }
}
```

> Success Returns (JSON)

```json
{
  "success": true,
  "_id": "1542hhjasdfhj234"
}
```

> Error Returns (JSON)

```json
{
  "error": "message"
}
```

This endpoint creates an order in a supplier system on behalf of a partner, by email.

### Quick Order Endpoint

`https://api.convictional.com/handlers/emails/quickOrder`

### Quick Order Example

`POST https://api.convictional.com/handlers/emails/quickOrder`

### Quick Order Properties

| Property    | Type      | Required  | Description                                          |
| ----------- | --------- | ----------| ---------------------------------------------------- |
| source      | string    | Required  | Email of the partner ordering (or sales rep).        |
| subject     | string    | Required  | CompanyId of the supplier / parent partner.          |
| items       | array     | Required  | Items on the order (properties below)                |
| address     | object    | Required  | Address to ship the order to.                        |

#### Items Properties

| Property    | Type      | Required  | Description                                          |
| ----------- | --------- | ----------| ---------------------------------------------------- |
| sku         | string    | Required  | SKU of the item.                                     |
| quantity    | number    | Required  | Number of the item being requested.                  |

#### Address Properties

| Property    | Type      | Required  | Description                                          |
| ----------- | --------- | ----------| ---------------------------------------------------- |
| name        | string    | Optional  | First and last name of the addressee                 |
| company     | string    | Optional  | Company name of the addressee                        |
| phone       | string    | Optional  | Phone number of the addressee                        |
| email       | string    | Optional  | Email of the addressee                               |
| type        | string    | Optional  | Type of the addressee                                |
| city        | string    | Optional  | City of the addressee                                |
| zip         | string    | Optional  | Zip code or postal code of the addressee             |
| state       | string    | Optional  | State, province or territory of the addressee        |
| country     | string    | Optional  | Country of the addressee                             |
| address     | string    | Optional  | Address of the addressee                             |
| addressTwo  | string    | Optional  | Address extra line of the addressee                  |