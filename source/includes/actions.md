# Actions
RPC endpoints that allow you to translate EDI documents, invite partners and more

## Sync

> Returns JSON:

```json
{
  "Successfully pushed getOrders to queue"
}
```

This endpoint allows you to initiate a sync method of your choosing.

### Endpoint URL
`https://api.convictional.com/sync/:method`

### HTTP Request example
`GET https://api.convictional.com/sync/getOrders`

### Sync Methods
| Method            | Description                                                                     |
| ----------------  |------------------------------------------------------------------------ --------|
| getOrders         | Trigger an event that will get the orders from all your trading partners        | 
| getOrderUpdates   | Trigger an event that will get order updates from your system                   |
| postOrders        | Trigger an event that will push orders from Convictional into your system       |
| postOrderUpdates  | Trigger an event that will push order updates to all your trading partners      |
| getProducts       | Trigger an event that will get products from your system                        |
| postProducts      | Trigger an event that will push products to your trading partners               |
| getProductUpdates | Trigger an event that will get inventory from your system                       |
| postProductUpdates| Trigger an event that will push inventory to your trading partners              |

## Translate

> Returns JSON structured like this:

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

### Endpoint URL
`https://api.convictional.com/translate`

### HTTP Request example

`POST https://api.convictional.com/translate`

### Translate Properties
| Property | Description                                                                           |
| -------- | ------------------------------------------------------------------------------------- |
| body     <td style="width:100%;"> The request body must contain an X12 EDI document in text </td>