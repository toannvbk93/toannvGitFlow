# getAdminUserList

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/admin | getAdminUserList | Graphql(POST) | Required |

Searches admin users and retrieves the list.

## Specification

### Request Query Schema

```text
query {
  getAdminUserList
}
```

### Request Header

Must set token to ‘Authorization’ HTTP header.
ex) Authorization: Bearer asdfasdfasdfasdfasdf.

### Result

<table>
<tr>
  <td>Success</td>
  <td><ul><li>Searches admin users and retrieves the list.</li></ul></td>
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
    getAdminUserList: {
      result : boolean,
      code : number,
      message : string,
      list : [AdminUser]
    }
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“getAdminUserList”],
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
    getAdminUserList: {
      result : true,
      code : 200,
      message : “OK.”,
      list : [
        { cuid : “1”, loginid : “Admin1”, name : “Admin1" },
        { cuid : “2”, loginid : “Admin2”, name : “Admin2” },
        { cuid : “3”, loginid : “Admin3”, name : “Admin3” },
      ]
    }
  }
}
```

