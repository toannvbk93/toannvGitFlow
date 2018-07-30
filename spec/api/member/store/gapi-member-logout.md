# gapi/logout

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/member | logout | Graphql (POST) | Required |

Logout from the store API server

## Specification

### Request Query Schema

```text
mutation {
  logout
}
```

### Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| \(none\) |  |  |  |

### Request Header

Must set token to ‘Authorization’ HTTP header.

ex\) Authorization: Bearer asdfasdfasdfasdfasdf

### Result
<table>
<tr>
  <td>Success</td>
  <td><ul><li> Logout from the store API server </li></ul></td>
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
    logout : 
    }
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“logout”],
    "data": { … },
    "errorType": "<Authentication Failure | Internal Server Error>",
    "locations": [{"line": #0, "column": #0}],
    "message": "<Session token is invalid | Page token is invalid | Sort parametor is invalid | Internal server error occured >"
  }
}
```

## Sample

```text
{
  data: {
    “logout” : {}
  }

  /* when the error occurs */
  “error” : {
    "path": [“logout”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

