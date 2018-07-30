# updateUserSetting

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /graphql | updateUserSetting | Graphql \(POST\) | Required |

Updates user-specific setting information

## Specification

### Request Query Schema

```text
mutation {
  updateUserSetting(userSetting: {
      isSafeSearch : true,
      hasR18Filter : true,
      ...
  })
}
```

### Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| userSetting | object! | - | The object to set values of User Setting information. |

### Request Header

Must set token to ‘Authorization’ HTTP header.

ex\) Authorization: Bearer asdfasdfasdfasdfasdf

### Result

| Success |  Update user's cofiguration information. |
| --- | --- |
| ErrorType | Authentication FailureSession token is invalidInvalid Argument Parametor is invalidInternal Server ErrorInternal server error occured |

#### Success Schema

```text
{
  data : {
    updateUserSetting : {
      result : boolean,
      code : number,
      message : string
    }
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“updateUserSetting”],
    "data": { … },
    "errorType": "<Authentication Failure | Invalid Argument  | Internal Server Error>",
    "locations": [{"line": #0, "column": #0}],
    "message": "<Session token is invalid | Parametor is invalid | Internal server error occured >"
  }
}
```

## Sample

```text
{
  data: {
    updateUserSetting : {
      result : (true | false),
      code : 200, // identifier of cause
      message : “OK”, // message to the client.
    }
  }

  /* when the error occurs */
  error: {
    "path": [“updateUserSetting”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

