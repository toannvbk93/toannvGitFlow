# getNoticeList

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /graphql | getNoticeList | Graphql | Required |

Retrieves a list of all notice information including non-public information.

## Specification

### Request Query Schema

```text
query {
  getNoticeList 
}
```

### Parameters

None

### Request Header

Must set token to ‘Authorization’ HTTP header.

ex\) Authorization: Bearer asdfasdfasdfasdfasdf

### Result

| Success | Return list of notice result |
| --- | --- |
| ErrorType | Authentication FailureSession token is invalidInternal Server Error |

#### Success Schema

```text
{
  data : {
    getNoticeList : {
      count : number,
      list : [Notice]
    }
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“getNoticeList”],
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
    getNoticeList : {
      count : 3,
      list : [
        {...},
        {...},
        {...},
      ]
    }
  }

  /* when the error occurs */
  error: {
    "path": [“getNoticeList”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

