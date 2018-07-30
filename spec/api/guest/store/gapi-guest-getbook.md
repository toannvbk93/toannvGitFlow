# getBook

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/guest | getBook | Graphql\(POST\) | Required |

Retrieves information of a book.

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
| bookId | ID! | - | The identifier of Book. |

### Request Header

must set token to ‘Authorization’ HTTP header.

ex\) Authorization: Bearer asdfasdfasdfasdfasdf

### Result

| Success | Retrieves information of a book. |
| --- | --- |
| ErrorType | Authentication FailureSession token is invalidInvalid ArgumentPage token is invalidSort parameter is invalidNot FoundInternal Server ErrorInternal server error occured |

#### Success Schema

```text
{
  data : {
    getBook : {
      book : Book
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
  data: {
      getBook : {
      result : (true | false),
      code : 200,
      message : “OK”,
      count : 5,
      item : {id : “90c9f4f0”, name : “週刊コミック 2018年 4月号”}
    }
  }

  /* when the error occurs */
  error: {
    "path": [“getBook”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }

}
```

