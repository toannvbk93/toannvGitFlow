# getFavoriteList

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /graphql | getFavoriteList | Graphql \(POST\) | Required |

Get a list of Books registered as user's favorite.

## Specification

### Request Query Schema

```text
query {
  getFavoriteList
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

| Success | Return a list of Books registered as user's favorite. |
| --- | --- |
| ErrorType | Authentication FailureSession token is invalidInternal Server ErrorInternal server error occured |

#### Success Schema

```text
{
  data : {
    getFavoriteList: [Book]
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“getFavoriteList”],
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
    getFavoriteList: [
        {...},
        {...},
        {...},
    ]
  }
  /* when the error occurs */
  error: {
    "path": [“getFavoriteList”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }

}
```

