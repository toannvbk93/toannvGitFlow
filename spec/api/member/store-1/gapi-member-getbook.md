# member/getBook

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/member | getBook | Graphql \(POST\) | Required |

Retrieves information of a book in the title.

## Specification

### Request Query Schema

```text
query {
  getBook (bookId : “<bookId>” )
}
```

### Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| bookId | ID! | - | The identifier of Book. |

### Request Header

Must set token to ‘Authorization’ HTTP header.

ex\) Authorization: Bearer asdfasdfasdfasdfasdf

### Result

| Success |  Retrieves information of a book in the title. |
| --- | --- |
| ErrorType | Authentication FailureSession token is invalidInvalid Argument Parametor is invalidInternal Server ErrorInternal server error occured |

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
    "path": [“getBook”],
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
    getBook : {
      book: {id : “90c9f4f0”, name : “週刊コミック 2018年 4月号”}
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

