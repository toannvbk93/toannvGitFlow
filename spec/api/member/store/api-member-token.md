# api-member-token

## Overview

| Endpoint | Type |
| --- | --- |
| /api/member/token | POST |

Get token

### Request

None

## Specification

### Parameters

None

### Request Header

Session id in cookie

### Response

```text
{
    token: {
      cognitoId: String
      cognitoIdToken : String,
      storeToken : string
    }
}
```

## Sample

```text
{
    “token”: {
      “cognitoId”: “”,
      “cognitoIdToken” : “”,
      “storeToken” : “”
    }
}
```

