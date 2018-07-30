# renewToken

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/admin | renewToken | Graphql\(POST\) | Required |

Re-retrieves the custom token necessary for using the API for administrators.

## Specification

### Request Query Schema

```text
mutation {
  renewToken
}
```

### Request Header

Must set token to ‘Authorization’ HTTP header. ex\) Authorization: Bearer asdfasdfasdfasdfasdf.

### Result

| Success | Re-obtains the custom token necessary for using the API for administrators. |
| --- | --- |
| ErrorType | Authentication FailureSession token is invalidInternal Server ErrorInternal server error occured |

#### Success Schema

```text
{
  data : {
    renewToken : {
      storeToken : string
    }
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“renewToken”],
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
    renewToken : {
      storeToken :  “asdfasdfasdfasdfasdf”
    }
  }

  /* when the error occurs */
  error: {
    "path": [“renewToken”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }

}
```

