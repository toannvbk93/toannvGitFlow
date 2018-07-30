# admin/getTitle

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/admin | getTitle | Graphql(POST) | Required |

Retrieves title information.

## Specification

### Request Query Schema

```text
query {
  getTitle (titleId : “<Title ID>”)
}
```

### Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| titleId | ID! | - | The identifier of Title. |
|  |  |  |  |

### Request Header

Must set token to ‘Authorization’ HTTP header.
ex) Authorization: Bearer asdfasdfasdfasdfasdf.

### Result

<table>
<tr>
  <td>Success</td>
  <td><ul><li>Retrieves title information.</li></ul></td>
</tr>
<tr>
  <td>ErrorType</td>
  <td>
    <ul>
      <li>Authentication Failure</li>
      <ul>
        <li>Session token is invalid</li>
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

```text
{
  data : {
    getTitle : {
      result : boolean,
      code : number,
      message : string,
      item : Title
    }
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“getTitle”],
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
    getTitle : {
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
    "path": [“getTitle”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

