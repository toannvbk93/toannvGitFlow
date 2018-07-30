# getUserSetting

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /graphql | getUserSetting | Graphql (POST) | Required |

Retrieves user-specific setting information that needs to be synchronized between the web or devices.

## Specification

### Request Query Schema

```text
query {
  getUserSetting
}
```

### Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| \(None\) |  |  |  |

### Request Header

Must set token to ‘Authorization’ HTTP header.

ex\) Authorization: Bearer asdfasdfasdfasdfasdf

### Result

<table>
<tr>
  <td>Success</td>
  <td><ul><li> Get user's configuration information that needs to be synchronized between WEB or login devices.</li></ul></td>
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
        <li>Page token is invalid</li>
        <li>Sort parametor is invalid</li>
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
    getUserSetting : {
      isSafeSearch : boolean,
      hasR18Filter : boolean,
      ...
    }
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“getUserSetting”],
    "data": { … },
    "errorType": "<Authentication Failure | Invalid Argument  | Internal Server Error>",
    "locations": [{"line": #0, "column": #0}],
    "message": "<Session token is invalid | Page token is invalid | Sort parametor is invalid | Internal server error occured >"
  }
}
```

## Sample

```text
{
  data: {
    getUserStatus : {
      isSafeSearch : true,
      hasR18Filter : true,
      ...
    }
  }

  /* when the error occurs */
  error: {
    "path": [“getUserStatus”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

