# guest/getNoticeList

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /graphql | getNoticeList | Graphql(POST) | Required |

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

ex) Authorization: Bearer asdfasdfasdfasdfasdf

### Result

<table>
<tr>
  <td>Success</td>
  <td><ul><li>Retrieves a list of notices.</li></ul></td>
</tr>
<tr>
  <td>ErrorType</td>
  <td>
    <ul>
      <li>Authentication Failure</li>
      <ul>
        <li>Session token is invalid</li>
      </ul>
      <li>Invalid Argument</li>
      <ul>
        <li>Page token is invalid</li>
        <li>Sort parameter is invalid</li>
      </ul>
      <li>Internal Server Error</li>
      <ul>
        <li>Internal server error occured</li>
      </ul>
    </ul>
  </td>
  </tr>
</table>

#### Success Schema
```

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

