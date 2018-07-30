# addConfig

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /graphql | addConfig | Graphql | Required |

Adds system setting information.

## Specification

### Request Query Schema

```text
mutation {
  addConfig (config : {
    ...
  })
}
```

### Parameters

| Name | Type | Description |
| --- | --- | --- |
| config | SystemConfig! | Object that storing Title information. |

### Request Header

Must set token to ‘Authorization’ HTTP header.

ex\) Authorization: Bearer asdfasdfasdfasdfasdf

### Result

<table>
<tr>
  <td>Success</td>
  <td><ul><li>Return added config infomation</li></ul></td>
</tr>
<tr>
  <td>ErrorType</td>
  <td>
    <ul>
      <li>Authentication FailureSession token is invalid</li>
      <li>Internal Server Error</li>
    </ul>
  </td>
  </tr>
</table>

#### Success Schema

```text
{
  data : {
    addConfig : {
      result : (true | false),
      code : 200, // identifier of cause
      message : “OK”, // message to the client.
      item : Config
    }
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“addConfig”],
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
    addConfig : {
      result : (true | false),
      code : 200, // identifier of cause message : “OK”, // message to the client.
      item : {
        ...
      }
    }
  }

  /* when the error occurs */
  error: {
    "path": [“addConfig”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

