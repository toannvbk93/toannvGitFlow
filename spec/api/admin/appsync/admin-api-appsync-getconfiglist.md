# getConfigList

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /graphql | getConfigList | Graphql | Required |

Retrieves a list of all system setting information.

## Specification

### Request Query Schema

```text
query {
  getConfigList 
}
```

### Parameters

None

### Request Header

Must set token to ‘Authorization’ HTTP header.

ex\) Authorization: Bearer asdfasdfasdfasdfasdf

### Result

<table>
<tr>
  <td>Success</td>
  <td><ul><li>Return list of config result</li></ul></td>
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
    getConfigList : {
      count : number,
      list : [Config]
    }
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“getConfigList”],
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
    getConfigList : {
      count : 3,
      list : [
        {...},
        {...},
        {...},
      ]
    }
  }

  /* when the error occurs */
  error: {
    "path": [“getConfigList”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

