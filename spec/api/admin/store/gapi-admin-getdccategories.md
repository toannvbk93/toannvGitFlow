# getDCCategories

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/admin | getDCCategories | Graphql(POST) | Required |

Retrieves all DC category information.

## Specification

### Request Query Schema

```text
query {
  getDCCategories
}
```

### Request Header

Must set token to ‘Authorization’ HTTP header.
ex) Authorization: Bearer asdfasdfasdfasdfasdf.

### Result

<table>
<tr>
  <td>Success</td>
  <td><ul><li>Retrieves all DC category information.</li></ul></td>
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
    getDCCategories: {
      list : [DCCategory]
    }
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“getDCCategory”],
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
    getDCCategories: {
      list : [
        {id : “00”, name : “sports”},
        {id : “01”, name : “news”},
        {id : “80”, name : “adult”}
      ]
    }
  }

  /* when the error occurs */
  error: {
    "path": [“getDCCategories”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

