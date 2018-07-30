# getConfig

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /graphql | getConfig | Graphql | Required |

Retrieves system setting information.

## Specification

### Request Query Schema

```text
query {
  getConfig (configId : “<Config ID>”)
}
```

### Parameters

| Name | Type | Description |
| --- | --- | --- |
| configId | ID! | The identifier of Config. |

### Request Header

Must set token to ‘Authorization’ HTTP header.

ex\) Authorization: Bearer asdfasdfasdfasdfasdf

### Result

| Success | Return config infomation |
| --- | --- |
| ErrorType | Authentication FailureSession token is invalidInternal Server Error |

#### Success Schema

```text
{
  data : {
    getConfig : Config
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“getConfig”],
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
    getConfig : {
        …
    }
  }

  /* when the error occurs */
  error: {
    "path": [“getConfig”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

