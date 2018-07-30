# search

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/guest | search | Graphql\(POST\) | Required |

Searches the titles by keywords and retrieves the results as a list of titles.

## API Schema

```text
enum SearchTarget {
  title
  author
  all
}

enum SortKey {
  new,
  title
}

type SearchOption {
  target: SearchTarget!,
  isSafeSearch: boolean
}

query {
  search (
     keyword : String!,
     option : SearchOption!,
     limit: Number,
     pageToken: String,
     sortkey : SortKey
  )
}
```

## Specification

### Request Query Schema

```text
query {
  search (
     keyword : “<keyword>”, (required)
     option : {
       target: “<title | author | all>, (required)
       isSafe: <true | false> (default: false)
     }
     ,limit: <number> (default: 10)
     ,pageToken: ”<pageToken>”,
     .sortkey : “<new | title>” 
  )
}
```

### Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| keyword | String! | - | Search keyword |
| option | SearchOption | - | type SearchOption {  target : SearchTarget  isSafeSearch : boolean!} |
| limit | Number | 10 | Maximum size of list items to get per query. |
| pageToken | String | - | The token to next page. |
| sortKey | SortKey | - | The name of the item to be sorted. Ascending order by the value of this key. |

#### Search Option Type

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| target | SearchTarget! | - | Keyword for search |
| isSafe | Boolean | false | Search option |

#### SeachTarget

| Param | Description |
| --- | --- |
| title | Search by title |
| author | Search by author |
| all | Search from All |

### Request Header

must set token to ‘Authorization’ HTTP header.

ex\) Authorization: Bearer asdfasdfasdfasdfasdf

### Result

| Success | Return list of search result |
| --- | --- |
| ErrorType | Authentication FailureSession token is invalidInvalid ArgumentPage token is invalidSort parameter is invalidInternal Server ErrorInternal server error occured |

#### Success Schema

```text
{
  data : {
    search : {
      count : number,
      list : [title],
      nextToken : string
    }
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“search”],
    "data": { … },
    "errorType": "<Authentication Failure | Invalid Argument  | Internal Server Error>",
    "locations": [{"line": #0, "column": #0}],
    "message": "<Session token is invalid | Page token is invalid | Sort parameter is invalid | Internal server error >"
  }
}
```

## Sample

```text
{
  data: {
    search : {
      count : 3,
      list : [
        {...},
        {...},
        {...},
      ],
      nextToken : “abcdabcdabcdabcdabcdabcdabcdabcd”
    }
  }

  /* when the error ocuurs */
  error: {
    "path": [“search”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

