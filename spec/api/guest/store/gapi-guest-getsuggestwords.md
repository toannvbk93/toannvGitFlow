# getSuggestWords

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/guest | getSuggestWords | Graphql(POST) | Required |

Retrieves suggest words corresponding to an arbitrary word.

## Specification

### Request Query Schema

```text
query {
  getSuggestWords (word : “<keyword>”)
}
```

### Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| word | string! | - | Keyword to be the source of the suggestion word. |

### Request Header

must set token to ‘Authorization’ HTTP header.

ex) Authorization: Bearer asdfasdfasdfasdfasdf

### Result

<table>
<tr>
  <td>Success</td>
  <td><ul><li>Retrieves suggest words corresponding to an arbitrary word.</li></ul></td>
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
        <li>Sort parameter is invalid</li>
      </ul>
      <li>Not Found</li>
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
    getSuggestWords : {
      suggestWords : [String]
    }
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“getSuggestWords”],
    "data": { … },
    "errorType": "<Authentication Failure | Invalid Argument  | Not Found | Internal Server Error>",
    "locations": [{"line": #0, "column": #0}],
    "message": "<Session token is invalid | Page token is invalid | Sort parameter is invalid | Internal server error occured >"
  }
}
```

## Sample

```text
{
  data : {
    getSuggestWords : [
        “女性自身”,
        “女性セブン”,
        “女性 コスメ”
      ]      
  }
  /* when the error occurs */
  error: {
    "path": [“getBookDownloadInfo”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

