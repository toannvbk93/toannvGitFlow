# deleteTitle

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/admin | deleteTitle | Graphql(POST) | Required |

Physically deletes title information. \(This is for emergency use. Please use update when deleting logically\)

## Specification

### Request Query Schema

```text
mutation {
  deleteTitle (titleId: “<Title ID>”)
}
```

### Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| title | ID! | - | The identifier of Title. |
|  |  |  |  |

### Request Header

Must set token to ‘Authorization’ HTTP header.
ex) Authorization: Bearer asdfasdfasdfasdfasdf.

### Result

<table>
<tr>
  <td>Success</td>
  <td><ul><li>Physically deletes title information.</li></ul></td>
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
    deleteTitle : {
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
    "path": [“deleteTitle”],
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
    deleteTitle : {
      result : true,
      code : 200,
      message : “OK.”
    }
  }

  /* when the error occurs */
  error: {
    "path": [“deleteTitle”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

