# getBookDownloadInfo

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/guest | getBookDownloadInfo | Graphql(POST) | Required |

Retrieves the required information to download/view books.

## Specification

### Request Query Schema

```text
query {
  getBookDownloadInfo (
    bookId : “<bookid>”
    userAgent : {
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
| userAgent | UserAgent! | - | type UserAgent {  platform : Platform!  version : string! } |

### Request Header

must set token to ‘Authorization’ HTTP header.

ex) Authorization: Bearer asdfasdfasdfasdfasdf

### Result

<table>
<tr>
  <td>Success</td>
  <td><ul><li>Retrieves the required information to download/view books.</li></ul></td>
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
        <li>Page token is invalid</li>
        <li>Sort parameter is invalid</li>
      </ul>
      <li>Not Found</li>
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

