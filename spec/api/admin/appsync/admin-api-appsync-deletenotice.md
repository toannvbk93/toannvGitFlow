# deleteNotice

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /graphql | deleteNotice | Graphql | Required |

Deletes specific notice information.

## Specification

### Request Query Schema

```text
mutation {
  deleteNotice (noticeId: “<Notice ID>”)
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
  <td><ul><li>Return delete success information</li></ul></td>
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
    deleteNotice : {
      result : (true | false),
      code : 200, // identifier of cause
      message : “OK”, // message to the client.
    }
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“deleteNotice”],
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
    deleteNotice : {
      result : true,
      code : 200,
      message : “OK.”
    }
  }

  /* when the error occurs */
  error: {
    "path": [“deleteNotice”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

