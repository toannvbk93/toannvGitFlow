# getStoreCategories

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/guest | getStoreCategories | Graphql\(POST\) | Required |

Retrieves all store categories. \(Argument candidates: top, recommend, ranking and orderby\)

## Specification

### Request Query Schema

```text
query {
  getStoreCategories (
    type : <top | recommend | ranking>,
    option : object
  )
}
```

### Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| type | StoreCategoryType! | - | top : トップページに表示するストアカテゴリ   ranking : ランキング情報 |
| userAgent | UserAgent! | - | type UserAgent {  platform : Platform!  version : string!} |

### Request Header

must set token to ‘Authorization’ HTTP header.

ex\) Authorization: Bearer asdfasdfasdfasdfasdf

### Result

| Success | Retrieves all store categories. |
| --- | --- |
| ErrorType | Authentication FailureSession token is invalidInvalid ArgumentPage token is invalidSort parameter is invalidNot FoundInternal Server ErrorInternal server error occured |

#### Success Schema

```text
{
  data : {
    getStoreCategories: {
      list : [StoreCategory]
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
    getStoreCategories : {
      list : [
        {id : “010”, code : “ranking”, name : “ランキング”
          itemList : [{...},{...},{...}]
        }, 
        {id : “020”, code : “comic”, name : “マンガ”
          itemList : [{...},{...},{...}]
        }, 
        {id : “030”, code : “sport”, name : “スポーツ誌”
          itemList : [{...},{...},{...}]
        }, 
        {id : “040”, code : “news”, name : “時事・ニュース”
          itemList : [{...},{...},{...}]
        }, 
        {id : “050”, code : “fasion”, name : “ファッション”
          itemList : [{...},{...},{...}]
        }, 
      ]   
    }
  }

  /* when the error occurs */
  error: {
    "path": [“getStoreCategories”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }

}
```

