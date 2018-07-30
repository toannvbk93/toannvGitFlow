# deleteAdminUser

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/admin | deleteAdminUser | Graphql(POST) | Required |

Deletes admin user information.

## Specification

### Request Query Schema

```text
mutation {
  deleteAdminUser (adminUserId: “<Administrator User ID>”)
}
```

### Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| adminUserId | ID! | - | The identifier of Admin User. |
|  |  |  |  |

### Request Header

Must set token to ‘Authorization’ HTTP header.
ex) Authorization: Bearer asdfasdfasdfasdfasdf.

### Result

<table>
<tr>
  <td>Success</td>
  <td><ul><li>Deletes admin user information.</li></ul></td>
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
    deleteAdminUser   : {
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
    "path": [deleteAdminUser],
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
    deleteAdminUser  : {
      result : true,
      code : 200,
      message : “OK.”
    }
  }

  /* when the error occurs */
  error: {
    "path": [“deleteAdminUser”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

