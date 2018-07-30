# addBook

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/admin | addBook | Graphql(POST) | Required |

Adds book information.

## Specification

### Request Query Schema

```text
mutation {
  addBook (book : {
    ...
  })
}
```

### Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| book | Book! | - | Object storing Book information. |
|  |  |  |  |

### Request Header

Must set token to ‘Authorization’ HTTP header.
ex) Authorization: Bearer asdfasdfasdfasdfasdf.

### Result

<table>
<tr>
  <td>Success</td>
  <td><ul><li>Add the information of book.</li></ul></td>
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
    addBook : {
      result : (true | false),
      code : 200, // identifier of cause
      message : “OK”, // message to the client.
      item : Book
    }
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“addBook”],
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
    addBook : {
      result : (true | false),
      code : 200, // identifier of cause
      message : “OK”, // message to the client.
      item : {
        ...
      }
    }
  }

  /* when the error occurs */
  error: {
    "path": [“addBook”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

