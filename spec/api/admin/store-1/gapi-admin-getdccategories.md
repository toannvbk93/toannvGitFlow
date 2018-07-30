# getDCCategories

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/admin | getDCCategories | Graphql\(POST\) | Required |

Retrieves all DC category information.

## Specification

### Request Query Schema

```text
query {
  getDCCategories
}
```

### Request Header

Must set token to ‘Authorization’ HTTP header. ex\) Authorization: Bearer asdfasdfasdfasdfasdf.

### Result

| Success | Retrieves all DC category information. |
| --- | --- |
| ErrorType | Authentication FailureSession token is invalidInternal Server ErrorInternal server error occured |

#### Success Schema

```text
{
  data : {
    getDCCategories: {
      list : [DCCategory]
    }
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“getDCCategory”],
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
    getDCCategories: {
      list : [
        {id : “00”, name : “sports”},
        {id : “01”, name : “news”},
        {id : “80”, name : “adult”}
      ]
    }
  }

  /* when the error occurs */
  error: {
    "path": [“getDCCategories”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

