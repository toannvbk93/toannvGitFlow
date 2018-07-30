# getBookList

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/member | getBookList | Graphql (POST) | Required |

Get a Book list related to a specific Title. Alternatively, it gets a list of books corresponding to the id.

## Specification

### Request Query Schema

```text
query {
  getBookList(titleId : “<Title ID>”)
}
```

### Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| titleId | string! | - | The identifier of the Title. |

### Request Header

Must set token to ‘Authorization’ HTTP header.

ex\) Authorization: Bearer asdfasdfasdfasdfasdf

### Result

<table>
<tr>
  <td>Success</td>
  <td><ul><li> Get a Book list related to a specific Title. </li></ul></td>
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
        <li> Parametor is invalid</li>
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
     book : Book
    }
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“getBookList”],
    "data": { … },
    "errorType": "<Authentication Failure | Invalid Argument  | Not Found | Internal Server Error>",
    "locations": [{"line": #0, "column": #0}],
    "message": "<Session token is invalid | Page token is invalid | Sort parametor is invalid | Internal server error occured >"
  }
}
```

## Sample

```text
{
  data: {
    getBookList : {
      count : 3,
      result : (true | false),
      code : 200, // identifier of cause
      message : “OK”, // message to the client.
      list : [
        {...},
        {...},
        {...},
      ]
    }
  }

  /* when the error occurs */
  error: {
    "path": [“getBookList”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

