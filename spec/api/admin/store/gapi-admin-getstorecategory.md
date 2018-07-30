# getStoreCategory

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/admin | getStoreCategory | Graphql(POST) | Required |

Retrieves a list of store category information. Store category includes top category, recommendation information, ranking information.

## Specification

### Request Query Schema

```text
query {
  getStoreCategory (storeCategoryId : “<Store Category ID>”)
}
```

### Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| storeCategoryId | ID! | - | The identifier of Store Category. |
|  |  |  |  |

### Request Header

Must set token to ‘Authorization’ HTTP header.
ex) Authorization: Bearer asdfasdfasdfasdfasdf.

### Result

<table>
<tr>
  <td>Success</td>
  <td><ul><li>Retrieves a list of store category information.</li></ul></td>
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
    getStoreCategory : {
      result : boolean,
      code : number,
      message : string,
      item : StoreCategory
    }
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“getStoreCategory”],
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
    getStoreCategory : {
      result : (true | false),
      code : 200, // identifier of cause
      message : “OK”, // message to the client.
      item : {
        …
      }
    }
  }

  /* when the error occurs */
  error: {
    "path": [“getStoreCategory”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

