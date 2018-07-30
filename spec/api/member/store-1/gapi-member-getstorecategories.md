# getStoreCategories

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/member | getStoreCategories | Graphql \(POST\) | Required |

Retrieves all store categories. \(Argument candidates: top, recommend, ranking and orderby\)

## Specification

### Request Query Schema

```text
query {
  getStoreCategories (
    type : <top | recommend | ranking>
    ,option : object
  )
}
```

### Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| type | StoreCategoryType! | - | top : トップページに表示するストアカテゴリ   “recommend” : おすすめ情報   ranking : ランキング情報 |
| userAgent | UserAgent! | - | UserAgent |

### Request Header

Must set token to ‘Authorization’ HTTP header.

ex\) Authorization: Bearer asdfasdfasdfasdfasdf

### Result

| Success |  Retrieves all store categories |
| --- | --- |
| ErrorType | Authentication FailureSession token is invalidInvalid Argument Parametor is invalidInternal Server ErrorInternal server error occured |

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
    "path": [“getStoreCategories”],
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
    getStoreCategories: {
      list : [
        {id : “010”, code : “ranking”, name : “ランキング”
        }, 
        {id : “020”, code : “comic”, name : “マンガ”
        }, 
        {id : “030”, code : “sport”, name : “スポーツ誌”
        }, 
        {id : “040”, code : “news”, name : “時事・ニュース”
        }, 
        {id : “050”, code : “fasion”, name : “ファッション”
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

