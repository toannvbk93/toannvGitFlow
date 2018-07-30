# admin/renewToken

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/admin | renewToken | Graphql(POST) | Required |

Re-retrieves the custom token necessary for using the API for administrators.

## Specification

### Request Query Schema

```text
mutation {
  renewToken
}
```

### Request Header

Must set token to ‘Authorization’ HTTP header.
ex) Authorization: Bearer asdfasdfasdfasdfasdf.

### Result

<table>
<tr>
  <td>Success</td>
  <td><ul><li>Re-obtains the custom token necessary for using the API for administrators.</li></ul></td>
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
    renewToken : {
      storeToken : string
    }
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“renewToken”],
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
    renewToken : {
      storeToken :  “asdfasdfasdfasdfasdf”
    }
  }

  /* when the error occurs */
  error: {
    "path": [“renewToken”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }

}
```

