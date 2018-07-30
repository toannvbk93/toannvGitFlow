# getSuggestWords

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/member | getSuggestWords | Graphql (POST) | Required |

Get a suggestion word corresponding to the specified keyword.

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

Must set token to ‘Authorization’ HTTP header.

ex\) Authorization: Bearer asdfasdfasdfasdfasdf

### Result
<table>
<tr>
  <td>Success</td>
  <td><ul><li>   Get a suggestion word corresponding to the specified keyword. </li></ul></td>
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
    "message": "<Session token is invalid | Page token is invalid | Sort parametor is invalid | Internal server error occured >"
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

