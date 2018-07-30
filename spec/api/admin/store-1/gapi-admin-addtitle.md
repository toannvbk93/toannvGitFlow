# addTitle

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/admin | addTitle | Graphql\(POST\) | Required |

Adds title information.

## Specification

### Request Query Schema

```text
mutation {
  addTitle (title : {
    ...
  })
}
```

### Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| title | Title! | - | Object that storing Title information. |
|  |  |  |  |

### Request Header

Must set token to ‘Authorization’ HTTP header. ex\) Authorization: Bearer asdfasdfasdfasdfasdf.

### Result

| Success | Adds title information. |
| --- | --- |
| ErrorType | Authentication FailureSession token is invalidInternal Server ErrorInternal server error occured |

#### Success Schema

```text
{
  data : {
    addTitle : {
      result : (true | false),
      code : 200, // identifier of cause
      message : “OK”, // message to the client.
      item : Title
    }
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“addTitle”],
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
    addTitle : {
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
    "path": [“addTitle”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

