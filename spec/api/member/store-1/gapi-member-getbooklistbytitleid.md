# getBookListByTitleId

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/member | getBookListByTitleId | Graphql \(POST\) | Not Required |

## Specification

### Request Query Schema

```text
query {
  getBookList(titleId : “<Title ID>”)
}
```

### Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| titleId | String! | - | The identifier of the Title. |
| limit | Number | 10 | Maximum size of list items to get per query. |
| pageToken | String | - | The token to next page. |
| sortKey | SortKey | - | The name of the item to be sorted. Ascending order by the value of this key. |

### Request Header

Must set token to ‘Authorization’ HTTP header.

ex\) Authorization: Bearer asdfasdfasdfasdfasdf

### Result

| Success |  Retrieves a list of titles. |
| --- | --- |
| ErrorType | Authentication FailureSession token is invalidInvalid Argument Parametor is invalidInternal Server ErrorInternal server error occured |

#### Success Schema

```text
{
  data : {
    getBookList: {
      count : number,
      result : boolean,
      code : number,
      message : string,
      list : [Book]
    }
  }
}
```

## Sample

```text
{
  data: {
    getBookList : {
      count : 3,
      result : (true | false),
      code : 200, // identifier of cause
      message : “OK”, // message to the client.
      list : [
        {...},
        {...},
        {...},
      ]
    }
  }

  /* when the error occurs */
  error: {
    "path": [“getBookList”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

