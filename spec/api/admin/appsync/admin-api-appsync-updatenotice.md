# updateNotice

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /graphql | updateNotice | Graphql | Required |

Updates specific notice information.

## Specification

### Request Query Schema

```text
mutation {
  updateNotice (notice : {
    ...
  })
}
```

### Parameters

| Name | Type | Description |
| --- | --- | --- |
| notice | Notice! | Object that storing Notice information. |

### Request Header

Must set token to ‘Authorization’ HTTP header.

ex\) Authorization: Bearer asdfasdfasdfasdfasdf

### Result

| Success | Return updated notice information |
| --- | --- |
| ErrorType | Authentication FailureSession token is invalidInternal Server Error |

#### Success Schema

```text
{
  data : {
    updateNotice : {
      result : (true | false),
      code : 200, // identifier of cause
      message : “OK”, // message to the client.
      item : Notice
    }
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“updateNotice”],
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
    updateNotice : {
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
    "path": [“updateNotice”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

