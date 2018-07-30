# getUserSetting

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /graphql | getUserSetting | Graphql \(POST\) | Required |

Retrieves user-specific setting information that needs to be synchronized between the web or devices.

## Specification

### Request Query Schema

```text
query {
  getUserSetting
}
```

### Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| \(None\) |  |  |  |

### Request Header

Must set token to ‘Authorization’ HTTP header.

ex\) Authorization: Bearer asdfasdfasdfasdfasdf

### Result

| Success |  Get user's configuration information that needs to be synchronized between WEB or login devices. |
| --- | --- |
| ErrorType | Authentication FailureSession token is invalidInvalid ArgumentPage token is invalidSort parametor is invalidInternal Server ErrorInternal server error occured |

#### Success Schema

```text
{
  data : {
    getUserSetting : {
      isSafeSearch : boolean,
      hasR18Filter : boolean,
      ...
    }
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“getUserSetting”],
    "data": { … },
    "errorType": "<Authentication Failure | Invalid Argument  | Internal Server Error>",
    "locations": [{"line": #0, "column": #0}],
    "message": "<Session token is invalid | Page token is invalid | Sort parametor is invalid | Internal server error occured >"
  }
}
```

## Sample

```text
{
  data: {
    getUserStatus : {
      isSafeSearch : true,
      hasR18Filter : true,
      ...
    }
  }

  /* when the error occurs */
  error: {
    "path": [“getUserStatus”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

