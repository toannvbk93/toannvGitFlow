# getNotice

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /graphql | getNotice | Graphql | Required |

## Specification

### Request Query Schema

```text
query {
  getNotice (noticeId : “<Notice ID>”)
}
```

### Parameters

| Name | Type | Description |
| --- | --- | --- |
| noticeId | ID! | The identifier of Notice. |

### Request Header

Must set token to ‘Authorization’ HTTP header.

ex\) Authorization: Bearer asdfasdfasdfasdfasdf

### Result

<table>
<tr>
  <td>Success</td>
  <td><ul><li>Return notice information</li></ul></td>
</tr>
<tr>
  <td>ErrorType</td>
  <td>
    <ul>
      <li>Authentication FailureSession token is invalid</li>
      <li>Internal Server Error</li>
    </ul>
  </td>
  </tr>
</table>

#### Success Schema

```text
{
  data : {
    getNotice : {
      result : boolean,
      code : number,
      message : string,
      item : Notice
    }
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“getNotice”],
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
    getNotice : {
      result : (true | false),
      code : 200, // identifier of cause
      message : “OK”, // message to the client.
      item : {
        …
      }
    }
  }

  /* when the error occurs */
  error: {
    "path": [“getNotice”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

