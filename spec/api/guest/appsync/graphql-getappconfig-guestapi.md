# getAppConfig

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /graphql | getAppConfig | Graphql\(POST\) | Required |

Retrieves the system setting information such as external site URL information.

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
| userAgent | UserAgent! | - | type UserAgent {  platform : Platform!  version : string! } |

### Request Header

Must set token to ‘Authorization’ HTTP header.

ex\) Authorization: Bearer asdfasdfasdfasdfasdf

### Result

| Success | Retrieves the system setting information such as external site URL information. |
| --- | --- |
| ErrorType | Authentication FailureSession token is invalidInvalid ArgumentPage token is invalidSort parameter is invalidInternal Server ErrorInternal server error occured |

#### Success Schema

```text
{
  data : {
    getStoreCategories: {
      list : [StoreCategory]
    }
  }
}

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
    "message": "<Session token is invalid | Page token is invalid | Sort parameter is invalid | Internal server error occured >"
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

