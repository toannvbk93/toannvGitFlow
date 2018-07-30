# getBookListByCategoryId

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/member | getBookListByCategoryId | Graphql (POST) | Required |

Retrieves a list of work titles under the following conditions.
  1. Title master that the user currently can view
  2. All title master
  3. Title master corresponding to the specified store category
In addition to the above conditions, the number of items and the sort order can be specified.
## Specification

### Request Query Schema

```text
query {
  getBookListByCategoryId (
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
| limit | Number! | 10 | Maximum size of list items to get per query. |
| pageToken | String | - | The token to next page. |
| sortKey | SortKey | - | The name of the item to be sorted. Ascending order by the value of this key. |


### Request Header

Must set token to ‘Authorization’ HTTP header.

ex\) Authorization: Bearer asdfasdfasdfasdfasdf

### Result

<table>
<tr>
  <td>Success</td>
  <td><ul><li> Get a Book list related to a specific Category. </li></ul></td>
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
    getBookListByCategoryId : {
      count : number,
      list : [Book],
      nextToken : string
    }
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“getBookListByCategoryId”],
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
    getBookListByCategoryId : {
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
    "path": [“getBookListByCategoryId”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

