# addDCCategory

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/admin | addDCCategory | Graphql\(POST\) | Required |

Adds DC category information.

## Specification

### Request Query Schema

```text
mutation {
  addDCCategory (dcCategory : {
    ...
  })
}
```

### Request Header

Must set token to ‘Authorization’ HTTP header. ex\) Authorization: Bearer asdfasdfasdfasdfasdf.

### Result

| Success | Adds DC category information. |
| --- | --- |
| ErrorType | Authentication FailureSession token is invalidInternal Server ErrorInternal server error occured |

#### Success Schema

```text
{
  data : {
    addDCCategory : {
      result : (true | false),
      code : 200, // identifier of cause
      message : “OK”, // message to the client.
      item : DCCategory
    }
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“addDCCategory”],
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
    addDCCategory : {
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
    "path": [“addDCCategory”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

