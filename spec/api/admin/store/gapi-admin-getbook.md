# admin/getBook

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/admin | getBook | Graphql(POST) | Required |

Retrieves book information.

## Specification

### Request Query Schema

```text
query {
  getBook (bookId : “<Book ID>”)
}
```

### Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| bookId | ID! | - | The identifier of Book. |
|  |  |  |  |

### Request Header

Must set token to ‘Authorization’ HTTP header.
ex) Authorization: Bearer asdfasdfasdfasdfasdf.

### Result

<table>
<tr>
  <td>Success</td>
  <td><ul><li>Retrieves book information.</li></ul></td>
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
    getBook : {
      result : boolean,
      code : number,
      message : string,
      item : Book
    }
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“getBook”],
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
    getBook : {
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
    "path": [“getBook”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

