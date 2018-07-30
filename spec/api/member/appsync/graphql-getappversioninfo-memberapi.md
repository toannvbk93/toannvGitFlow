# member/getAppVersionInfo

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /graphql | getAppVersionInfo | Graphql (POST) | Required |

Get the latest version information of the native application. It is necessary to specify the type of application \(iPhone / Android\).

## Specification

### Request Query Schema

```text
query {
  getAppVersionInfo(
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
| userAgent | UserAgent! | - | UserAgent |

### Request Header

Must set token to ‘Authorization’ HTTP header.

ex\) Authorization: Bearer asdfasdfasdfasdfasdf

### Result

<table>
<tr>
  <td>Success</td>
  <td><ul><li> Retrieves the latest version information \(force update\) of the app.</li></ul></td>
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
        <li>Sort parametor is invalid</li>
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
    getAppVersionInfo : {
      version : string,
      mustUpdate : boolean
    }
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“getAppVersionInfo”],
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
  data : {
    getAppVersionInfo : {
      version : “1.01”,
      mustUpdate : true
    }
  }

  /* when the error occurs */
  error: {
    "path": [“getAppVersionInfo”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }

}
```

