# getBookDownloadInfo

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/member | getBookDownloadInfo | Graphql \(POST\) | Required |

Retrieves the required information to download/view books.

## Specification

### Request Query Schema

```text
query {
  getBookDownloadInfo (
    bookId : “<bookid>”
    ,userAgent : {
      platform : <iPhone | Android | Browser>
      osVersion : “<OS Version>”
    }
  )
}
```

### Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| bookId | ID! | - | The identifier of Book. |
| userAgent | UserAgent! | - | UserAgent |

### Request Header

Must set token to ‘Authorization’ HTTP header.

ex\) Authorization: Bearer asdfasdfasdfasdfasdf

### Result

| Success |  The required information to download/view books. |
| --- | --- |
| ErrorType | Authentication FailureSession token is invalidInvalid Argument Parametor is invalidInternal Server ErrorInternal server error occured |

#### Success Schema

```text
{
  data : {
    getBookDownloadInfo : {
      url: string, // ウェブとアプリで異なる
      decryptKey: string
    }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“getBookDownloadInfo”],
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
    getBookDownloadInfo : {
      url: “”,
      decryptKey: “”
    }
  }

  /* when the error occurs */
  error: {
    "path": [“getBookDownloadInfo”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

