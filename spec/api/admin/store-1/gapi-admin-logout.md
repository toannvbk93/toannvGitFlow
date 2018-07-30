# logout

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/admin | logout | Graphql\(POST\) | Required |

Logs out from the store API server for administrators.

## Specification

### Request Query Schema

```text
mutation {
  logout
}
```

### Request Header

Must set token to ‘Authorization’ HTTP header. ex\) Authorization: Bearer asdfasdfasdfasdfasdf.

### Result

| Success | Log out from the store API server for administrators. |
| --- | --- |
| ErrorType | Authentication FailureSession token is invalidPage token is invalidSort parametor is invalidInternal Server ErrorInternal server error occured |

#### Success Schema

```text
{
  data : {
    logout : 
    }
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“logout”],
    "data": { … },
    "errorType": "<Authentication Failure | Internal Server Error>",
    "locations": [{"line": #0, "column": #0}],
    "message": "<Session token is invalid | Page token is invalid | Sort parametor is invalid | Internal server error occured >"
  }
}
```

## Sample

```text
{
  data: {
    “logout” : {}
  }

  /* when the error occurs */
  “error” : {
    "path": [“logout”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

