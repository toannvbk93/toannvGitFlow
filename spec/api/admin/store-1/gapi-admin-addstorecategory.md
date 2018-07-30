# addStoreCategory

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/admin | addStoreCategory | Graphql\(POST\) | Required |

Adds store category information.

## Specification

### Request Query Schema

```text
mutation {
  addStoreCategory (storeCategory : {
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

Must set token to ‘Authorization’ HTTP header. ex\) Authorization: Bearer asdfasdfasdfasdfasdf.

### Result

| Success | Adds store category information. |
| --- | --- |
| ErrorType | Authentication FailureSession token is invalidInternal Server ErrorInternal server error occured |

#### Success Schema

```text
{
  data : {
    addStoreCategory  : {
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
    "path": [“addStoreCategory”],
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
    addStoreCategory : {
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
    "path": [“addStoreCategory”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

