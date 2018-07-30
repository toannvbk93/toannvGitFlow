# updateUserSetting

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /graphql | updateUserSetting | Graphql (POST) | Required |

Updates user-specific setting information

## Specification

### Request Query Schema

```text
mutation {
  updateUserSetting(userSetting: {
      isSafeSearch : true,
      hasR18Filter : true,
      ...
  })
}
```

### Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| userSetting | object! | - | The object to set values of User Setting information. |

### Request Header

Must set token to ‘Authorization’ HTTP header.

ex\) Authorization: Bearer asdfasdfasdfasdfasdf

### Result
<table>
<tr>
  <td>Success</td>
  <td><ul><li>  Update user's cofiguration information. </li></ul></td>
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
    updateUserSetting : {
      result : boolean,
      code : number,
      message : string
    }
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“updateUserSetting”],
    "data": { … },
    "errorType": "<Authentication Failure | Invalid Argument  | Internal Server Error>",
    "locations": [{"line": #0, "column": #0}],
    "message": "<Session token is invalid | Parametor is invalid | Internal server error occured >"
  }
}
```

## Sample

```text
{
  data: {
    updateUserSetting : {
      result : (true | false),
      code : 200, // identifier of cause
      message : “OK”, // message to the client.
    }
  }

  /* when the error occurs */
  error: {
    "path": [“updateUserSetting”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

