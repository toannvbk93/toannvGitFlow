# addAdminUser

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/admin | addAdminUser | Graphql\(POST\) | Required |

Adds admin user information.

## Specification

### Request Query Schema

```text
mutation {
  addAdminUser (adminUser : {
    ...
  })
}
```

### Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| adminUser | AdminUser! | - | Object storing Admin User information. |
|  |  |  |  |

### Request Header

Must set token to ‘Authorization’ HTTP header. ex\) Authorization: Bearer asdfasdfasdfasdfasdf.

### Result

| Success | Add the information of Admin User. |
| --- | --- |
| ErrorType | Authentication FailureSession token is invalidInternal Server ErrorInternal server error occured |

#### Success Schema

```text
{
  data : {
    addAdminUser : {
      result : (true | false),
      code : 200, // identifier of cause
      message : “OK”, // message to the client.
      item : AdminUser
    }
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [addAdminUser],
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
    addAdminUser : {
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
    "path": [addAdminUser],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

