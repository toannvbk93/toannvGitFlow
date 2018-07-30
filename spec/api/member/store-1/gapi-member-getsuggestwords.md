# getSuggestWords

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/member | getSuggestWords | Graphql \(POST\) | Required |

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

| Success |  Get a suggestion word corresponding to the specified keyword. |
| --- | --- |
| ErrorType | Authentication FailureSession token is invalidInvalid Argument Parametor is invalidSort parametor is invalidInternal Server ErrorInternal server error occured |

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

