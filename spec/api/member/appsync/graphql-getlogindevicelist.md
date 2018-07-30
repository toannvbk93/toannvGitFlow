# getLoginDeviceList

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /graphql | getLoginDeviceList | Graphql (POST) | Required |

Retrieves a list of currently logged-in devices.

## Specification

### Request Query Schema

```text
query {
  getLoginDeviceList
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
  <td><ul><li>Get the list of user's currently logged-in devices.</li></ul></td>
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
data : {
    getLoginDeviceList : [{
        id : string,
        name : string
    }]
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“getLoginDeviceList”],
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
    getLoginDeviceList : {
      result : {
        result : (true | false),
        code : 200, // identifier of cause
        message : “OK”, // message to the client.
      },
      list : [
        {id : “8c8590c9f4c5”, name : “iPhone 6,2”},
        {id : “8c8590c9f4d2”, name : “iPhone x”},
        {id : “8c8590c9f4ef”, name : “iPhone SE 2”},
      ],
    }
  }

  /* when the error occurs */
  error: {
    "path": [“getLoginDeviceList ”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

