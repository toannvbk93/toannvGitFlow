# api/member/renewToken

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/member | renewToken | Graphql \(POST\) | Required |

Renew the token for using the API. If it’s already logged in to T-Magazine, check the validity of the TSUTAYA side token. If processing fails, it is necessary to log in again from T-Magazine.

## Specification

### Request Query Schema

```text
mutation {
  renewToken
}
```

### Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| \(none\) |  |  |  |

### Request Header

must set token to ‘Authorization’ HTTP header.

ex\) Authorization: Bearer asdfasdfasdfasdfasdf

### Result

| Success |  Renew the token for using the API. |
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
```

