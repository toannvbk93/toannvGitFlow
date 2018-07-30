# getAppVersionInfo

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /graphql | getAppVersionInfo | Graphql \(POST\) | Required |

Get the latest version information of the native application. It is necessary to specify the type of application \(iPhone / Android\).

## Specification

### Request Query Schema

```text
query {
  getAppVersionInfo(
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

| Success |  Retrieves the latest version information \\(force update\\) of the app. |
| --- | --- |
| ErrorType | Authentication FailureSession token is invalidInvalid ArgumentPage token is invalidSort parametor is invalidInternal Server ErrorInternal server error occured |

#### Success Schema

```text
{
  data : {
    getAppVersionInfo : {
      version : string,
      mustUpdate : boolean
    }
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“getAppVersionInfo”],
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
  data : {
    getAppVersionInfo : {
      version : “1.01”,
      mustUpdate : true
    }
  }

  /* when the error occurs */
  error: {
    "path": [“getAppVersionInfo”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }

}
```

