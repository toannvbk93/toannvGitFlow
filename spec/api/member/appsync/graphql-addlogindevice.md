# addLoginDevice

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /graphql | addLoginDevice | Graphql (POST) | Required |

Adds a device information as currently logged in device.\(This API will not be affected by the number limit of devices.\)

## Specification

### Request Query Schema

```text
mutation {
  addLoginDevice(
    deviceId: “<Device ID>”
    ,deviceName: “<Device Name>”
  )
}
```

### Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| deviceId | String! | - | Client-side Identifier of Login Device. |
| deviceName | String! | - | the name of Login Device. |

### Request Header

Must set token to ‘Authorization’ HTTP header.

ex\) Authorization: Bearer asdfasdfasdfasdfasdf

### Result

<table>
<tr>
  <td>Success</td>
  <td><ul><li>Adds a device information as currently logged in device</li></ul></td>
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
    addLoginDevice : {
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
    "path": [“addLoginDevice”],
    "data": { … },
    "errorType": "<Authentication Failure| Internal Server Error>",
    "locations": [{"line": #0, "column": #0}],
    "message": "<Session token is invalid | Internal server error occured >"
  }
}
```

## Sample

```text
{
  data: {
    addLoginDevice : {
      result : false,
      code : 9999,
      message : “”
    }
  }

  /* when the error occurs */
  error: {
    "path": [“addLoginDevice”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

