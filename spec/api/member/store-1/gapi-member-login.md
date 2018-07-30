# login

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/member | login | Graphql \(POST\) | Not Required |

Login to the store API server.

## Specification

### Request Query Schema

```text
mutation {
  login(
    tmid: "<t_magazine_user_id>", 
    requestToken: "<request_token>"
  )
}
```

### Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| tmid | String! | - | TMID\(nonce key\) |
| requestToken | string! | - | Request Token of TSUTAYA API |

### Request Header

Not Required

### Result

| Success |  Return session token |
| --- | --- |
| ErrorType | Authentication FailureSession token is invalidInternal Server ErrorInternal server error occured |

#### Success Schema

```text
{
  data : {
    login : {
      cognitoId: string
      cognitoIdToken : string,
      storeToken : string
    }
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“login”],
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
    login : {
      cognitoId: “”,
      cognitoIdToken : “”,
      storeToken : “”
    }
  }

  /* when the error occurs */
  error: {
    "path": [“login”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

