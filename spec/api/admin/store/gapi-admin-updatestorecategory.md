# updateStoreCategory

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/admin | updateStoreCategory | Graphql(POST) | Required |

Updates store category information.

## Specification

### Request Query Schema

```text
mutation {
  updateStoreCategory (storeCategory : {
    ...
  })
}
```

### Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| storeCategory | StoreCategory! | - | Object storing Store Category information. |
|  |  |  |  |

### Request Header

Must set token to ‘Authorization’ HTTP header.
ex) Authorization: Bearer asdfasdfasdfasdfasdf.

### Result

<table>
<tr>
  <td>Success</td>
  <td><ul><li>Updates store category information.</li></ul></td>
</tr>
<tr>
  <td>ErrorType</td>
  <td>
    <ul>
      <li>Authentication Failure</li>
      <ul>
        <li>Session token is invalid</li>
      </ul>
      <li>Internal Server Error</li>
      <ul>
        <li>Internal server error occured</li>
      </ul>
    </ul>
  </td>
  </tr>
</table>

#### Success Schema

```text
{
  data : {
    updateStoreCategory : {
      result : (true | false),
      code : 200, // identifier of cause
      message : “OK”, // message to the client.
      item : StoreCategory
    }
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“updateStoreCategory”],
    "data": { … },
    "errorType": "<Authentication Failure | Internal Server Error>",
    "locations": [{"line": #0, "column": #0}],
    "message": "<Session token is invalid | Internal server error occured >"
  }
}
```

## Sample

```text
{
  data: {
    updateStoreCategory  : {
      result : (true | false),
      code : 200, // identifier of cause
      message : “OK”, // message to the client.
      item : {
        ...
      }
    }
  }

  /* when the error occurs */
  error: {
    "path": [updateStoreCategory ],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

