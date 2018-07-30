# admin/getTitleList

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/admin | getTitleList | Graphql\(POST\) | Required |

Retrieves a list of titles under specified conditions.

## Specification

### Request Query Schema

```text
query {
  getTitleList (
    keyword : “<keyword>”
    ,dcCategory: “<DC Category ID>”
    ,storeCategory: “<Store Category ID>”
    ,limit: <number> 
    ,pageToken:”<pageToken>” 
    ,sortkey : <new | title>
  )
}
```

### Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| keyword | String! | - | Search keyword for title |
| dcCategory | ID | - | The identifier of DC Category. |
| storeCategory | ID | - | The identifier of Store Category. |
| limit | Number | 10 | Maximum size of list items to get per query. |
| pageToken | String | - | The token to next page |
| sortKey | String | "new" | The name of the item to be sorted. Ascending order by the value of this key. |
|  |  |  |  |

### Request Header

Must set token to ‘Authorization’ HTTP header. ex\) Authorization: Bearer asdfasdfasdfasdfasdf.

### Result

| Success | Retrieves a list of titles under specified conditions. |
| --- | --- |
| ErrorType | Authentication FailureSession token is invalidInvalid ArgumentPage token is invalidSort parametor is invalidInternal Server ErrorInternal server error occured |

#### Success Schema

```text
{
  data : {
    getTitleList : {
      count : number,
      list : [Title],
      nextToken : string
    }
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“getTitleList”],
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
    getTitleList : {
      count : 3,
      list : [
        {...},
        {...},
        {...},
      ],
      nextToken : “abcdabcdabcdabcdabcdabcdabcdabcd”
    }
  }

  /* when the error occurs */
  error: {
    "path": [“getTitleList”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

