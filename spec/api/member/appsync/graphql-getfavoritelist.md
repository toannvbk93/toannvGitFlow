# getFavoriteList

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /graphql | getFavoriteList | Graphql (POST) | Required |

Get a list of Books registered as user's favorite.

## Specification

### Request Query Schema

```text
query {
  getFavoriteList
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
  <td><ul><li>Return a list of Books registered as user's favorite.</li></ul></td>
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
    getFavoriteList: [Book]
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“getFavoriteList”],
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
    getFavoriteList: [
        {...},
        {...},
        {...},
    ]
  }
  /* when the error occurs */
  error: {
    "path": [“getFavoriteList”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }

}
```

