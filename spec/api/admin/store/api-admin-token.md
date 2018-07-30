# admin/token\(POST\)

## Overview

| Endpoint | Name |Type |
| --- | --- | --- |
| /api/admin/token | token (Administrator) | POST |

Re-retrieves the token necessary for using the API.

## Specification

### Parameters

None

### Request

None

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