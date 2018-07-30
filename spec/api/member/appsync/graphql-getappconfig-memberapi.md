# getAppConfig

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /graphql | getAppConfig | Graphql \(POST\) | Required |

Get a list of external site URL information. The list contains all URL. The list has key and value pair. Key is identifier of url, value is URL and label

## Specification

### Request Query Schema

```text
query {
  getAppConfig (
    userAgent : {
      platform : <iPhone | Android | Browser>
      osVersion : “<OS Version>”
    }
  )
}
```

### Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| userAgent | UserAgent! | - | UserAgent |

### Request Header

Must set token to ‘Authorization’ HTTP header.

ex\) Authorization: Bearer asdfasdfasdfasdfasdf

### Result

| Success | Get a list of external site URL information. |
| --- | --- |
| ErrorType | Authentication FailureSession token is invalidInvalid ArgumentPage token is invalidSort parametor is invalidInternal Server ErrorInternal server error occured |

#### Success Schema

```text
{
  data : {
    getAppConfig : {
      config: object
    }
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“getAppConfig”],
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
    getAppConfig : {
      “xxxURL” : “https://~”,
      “yyyURL” : “https://~”,
      ...
    }
  }

  /* when the error occurs */
  error: {
    "path": [“getURLList”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

