# member/renewToken

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/member | renewToken | Graphql (POST) | Required |

Renew the token for using the API. If it’s already logged in to T-Magazine, check the validity of the TSUTAYA side token. If processing fails, it is necessary to log in again from T-Magazine.

## Specification

### Request Query Schema

```text
mutation {
  renewToken
}
```

### Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| \(none\) |  |  |  |

### Request Header

must set token to ‘Authorization’ HTTP header.

ex\) Authorization: Bearer asdfasdfasdfasdfasdf

### Result
<table>
<tr>
  <td>Success</td>
  <td><ul><li> Renew the token for using the API. </li></ul></td>
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
```

