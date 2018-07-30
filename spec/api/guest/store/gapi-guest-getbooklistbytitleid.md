# getBookListByTitleId

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/guest | getBookListByTitleId | Graphql\(POST\) | Required |

Retrieves a list of books corresponding to the title.

## Specification

### Request Query Schema

```text
query {
  getBookList(
   titleId : <titleId>, 
  )
}
```

### Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| titleId | ID! | - | The identifier of the Title. |
| limit | Number | 10 | Maximum size of list items to get per query. |
| pageToken | String | - | The token to next page. |
| sortKey | SortKey | - | The name of the item to be sorted. Ascending order by the value of this key. |

### Request Header

must set token to ‘Authorization’ HTTP header.

ex\) Authorization: Bearer asdfasdfasdfasdfasdf

### Result

| Success | Retrieves a list of books corresponding to the title. |
| --- | --- |
| ErrorType | Authentication FailureSession token is invalidInvalid ArgumentTitleId is invalidNot FoundInternal Server Error |

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

#### Error Schema

```text
{
  error: {
    "path": [“getBookList”],
    "data": { … },
    "errorType": "<Authentication Failure | Invalid Argument  | Not Found | Internal Server Error>",
    "locations": [{"line": #0, "column": #0}],
    "message": "<Session token is invalid | TitleId is invalid | Internal server error occured >"
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
        {“_id”:...,"craetedAt"：YYYYMMDD HH:MM:SS,"updatedAt"：YYYYMMDD HH:MM:SS,"isActive"：1,"title"：第一話,"kana"：だいいちわ,"publishStartDateTime"：YYYYMMDD HH:MM:SS,"publishEndDateTime"：YYYYMMDD HH:MM:SS,"explanation"：...,"imagePath"：...,"targetRole"：t-magazine,"genericCode"[{“jdbc”：...,”iban”：...,”jan”：...}],"additionalInfo"[{dc[{“price”：90,”downloadLimit”：30,”filesize”：1075339,”master”：1,”permitId”：”00000000”,”format”：”00000000”,”permitStart”：YYYYMMDD HH:MM:SS,”permitEnd”：YYYYMMDD HH:MM:SS,”jdcn”：...,”publisherContentCode”：...,”magazineNumber”：YYYYMMDD,”openTime”：YYYYMMDD HH:MM:SS,”rowindex”：0}],dc[{“targetRole”:premium}]}]},
        {...},
        {...},
      ]
    }
  }

  /* when the error occurs */
  error: {
    "path": [“search”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

