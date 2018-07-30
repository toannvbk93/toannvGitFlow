# getNoticeList

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /graphql | getNoticeList | Graphql\(POST\) | Required |

Retrieves a list of notices.

## Specification

### Request Query Schema

```text
query {
  getNoticeList(
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

| Success | Retrieves a list of notices. |
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
    getNoticeList : [{
        id : string,
        title : string,
        message : string,
        posted : Date
    }] // 0件のときはからの配列
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“getNoticeList”],
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
    getNoticeList : [
      { id : “1”, title : “TITLE ”, message : “...”, posted : “2018-05-18T13:15:45.000Z” },
      { id : “2”, title : “TITLE ”, message : “...”, posted : “2018-05-18T13:15:45.000Z” },
      { id : “3”, title : “TITLE ”, message : “...”, posted : “2018-05-18T13:15:45.000Z” },
    ]
  }

  /* when the error occurs */
  error: {
    "path": [“getNoticeList ”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

