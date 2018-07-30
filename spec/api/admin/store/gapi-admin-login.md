# gapi/admin/login

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/admin | login | Graphql(POST) | Required |

Logs in to the store API server for administrators.

## Specification

### Request Query Schema

```text
mutation {
  login(
    userId: "<administrator_user_id>"
    ,password: "<password>"
  )
}
```

### Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| userId | String! | - | The identifier of administrator user. |
| password | String! | - | Password |
|  |  |  |  |

### Result

<table>
<tr>
  <td>Success</td>
  <td><ul><li>Log in to the store API server for administrators.</li></ul></td>
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
    login : {
      cognitoId: string
      cognitoIdToken : string,
      storeToken : string
    }
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“login”],
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
    login : {
      cognitoId: “”,
      cognitoIdToken : “”,
      storeToken : “”
    }
  }

  /* when the error occurs */
  error: {
    "path": [“login”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

