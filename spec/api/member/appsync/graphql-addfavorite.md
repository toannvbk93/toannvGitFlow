# addFavorite

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /graphql | addFavorite | Graphql (POST) | Required |

Adds a specific title to my list.

## Specification

### Request Query Schema

```text
mutation {
  addFavorite (bookId : “<Book ID>”)
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
  <td><ul><li>Adds a specific title to my list.</li></ul></td>
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
    addFavorite : {
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
    "path": [“addFavorite”],
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
    addFavorite : {
      result : (true | false),
      code : 200, // identifier of cause
      message : “OK”, // message to the client.
    }
  }

  /* when the error occurs */
  error: {
    "path": [“addFavorite”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

