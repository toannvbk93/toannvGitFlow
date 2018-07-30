# getBookListByCategoryId

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/guest | getBookListByCategoryId | Graphql\(POST\) | Required |

Retrieves a list of books corresponding to the store categories.

## Specification

### Request Query Schema

```text
query {
  getTitleList (
    storeCategory : “<storeCategoryId>”
    ,limit: <limitNumber>
    ,pageToken: <pageToken>
    ,sortkey : <new | title>
  )
}
```

### Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| storeCategoryId | ID! | - | The  Store Category identifier. Find the Title from among the set categories. |
| limit | Number | 10 | Maximum size of list items to get per query. |
| pageToken | String | - | The token to next page. |
| sortKey | SortKey | - | The name of the item to be sorted. Ascending order by the value of this key. |

### Request Header

must set token to ‘Authorization’ HTTP header.

ex\) Authorization: Bearer asdfasdfasdfasdfasdf

### Result

| Success | Retrieves a list of books corresponding to the store categories. |
| --- | --- |
| ErrorType | Authentication FailureSession token is invalidInvalid ArgumentPage token is invalidSort parameter is invalidInternal Server ErrorInternal server error occured |

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
    "message": "<Session token is invalid | Page token is invalid | Sort parameter is invalid | Internal server error occured >"
  }
}
```

## Sample

```text
{
  data: {
    getTitleList : {
    search : {
      count : 3,
      list : [
        {"_id"：...,"craetedAt"：YYYYMMDD HH:MM:SS,"updatedAt"：YYYYMMDD HH:MM:SS,"active"：1,"title"：○○物語,"kana"：まるまるものがたり,"explanation"：まるまるものがたり<br>...,"imagePath"：/img/data/00000000,"targetRole"：t-magazine,"sourceType"：ds,"publishDate"：YYYYMMDD HH:MM:SS,"additionalInfo":[
{dc：[{“dataId”:”00000000”,”genreCode”:0001-0002-FFFF,”r18Rating”:0,”}]}
ccc：[{genreCode：["1":0000,”2”:0000,”3”:0000],productUrl：[“stockSearchUrl”：...,"relatedBookSearchUrl"：...]}]
]},
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

