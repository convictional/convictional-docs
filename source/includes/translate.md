# EDI
RPC endpoints that allow you to translate and transmit EDI documents.

## POST - Translate

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