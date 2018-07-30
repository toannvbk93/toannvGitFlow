# deleteStoreCategory

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/admin | deleteStoreCategory | Graphql\(POST\) | Required |

Deletes store category information.

## Specification

### Request Query Schema

```text
mutation {
  deleteStoreCategory (storeCategoryId: “<Store Category ID>”)
}
```

### Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| storeCategoryId | ID! | - | The identifier of Store Category. |
|  |  |  |  |

### Request Header

Must set token to ‘Authorization’ HTTP header. ex\) Authorization: Bearer asdfasdfasdfasdfasdf.

### Result

| Success | Deletes store category information. |
| --- | --- |
| ErrorType | Authentication FailureSession token is invalidInternal Server ErrorInternal server error occured |

#### Success Schema

```text
{
  data : {
    deleteStoreCategory   : {
      result : (true | false),
      code : 200, // identifier of cause
      message : “OK”, // message to the client.
    }
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [deleteStoreCategory ],
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
    deleteStoreCategory : {
      result : true,
      code : 200,
      message : “OK.”
    }
  }

  /* when the error occurs */
  error: {
    "path": [“deleteStoreCategory”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

