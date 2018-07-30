# member/getBook

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/member | getBook | Graphql (POST) | Required |

Retrieves information of a book in the title.

## Specification

### Request Query Schema

```text
query {
  getBook (bookId : “<bookId>” )
}
```

### Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| bookId | ID! | - | The identifier of Book. |

### Request Header

Must set token to ‘Authorization’ HTTP header.

ex\) Authorization: Bearer asdfasdfasdfasdfasdf

### Result

<table>
<tr>
  <td>Success</td>
  <td><ul><li>  Retrieves information of a book in the title. </li></ul></td>
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
    "path": [“getBook”],
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
  data : {
    getBook : {
      book: {id : “90c9f4f0”, name : “週刊コミック 2018年 4月号”}
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

