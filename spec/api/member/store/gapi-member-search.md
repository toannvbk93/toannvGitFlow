# gapi/search

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/member | search | Graphql (POST) | Required |

Searches the titles by keywords and retrieves the results as a list of titles.

## Specification

### Request Query Schema

```text
query {
  search (
     keyword : “<keyword>” (Required)
     ,option : {
       target: <title | publisher | detail>
       isSafeSearch: true ( default: false )
     } 
     ,limit: <number> 
     ,pageToken:”<pageToken>” 
     ,sortkey : <new | title>
  )
}
```

### Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| keyword | String! | - | Keyword for search |
| option | SearchOption | - | Search option |
| limit | Number | - | Maximum size of list items to get per query. |
| pageToken | String | - | The token to next page. |
| sortKey | String | - | The name of the item to be sorted. Ascending order by the value of this key. |
|  |  |  |  |

#### Search Option Type

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| target | SearchTarget! | - | Keyword for search |
| isSafe | Boolean | false | Search option |

#### SeachTarget

| Param | Description |
| --- | --- |
| title | Search by title |
| author | Search by author |
| all | Search from All |

### Request Header

must set token to ‘Authorization’ HTTP header.

ex\) Authorization: Bearer asdfasdfasdfasdfasdf

### Result
<table>
<tr>
  <td>Success</td>
  <td><ul><li> Return list of search result </li></ul></td>
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
    search : {
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
    "path": [“search”],
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
    search : {
      count : 3,
      list : [
        {...},
        {...},
        {...},
      ],
      nextToken : “abcdabcdabcdabcdabcdabcdabcdabcd”
    }
  }

  /* when the error occurs */
  error: {
    "path": [“search”],
    "data": { … },
    "errorType": "Authentication Failure",
    "locations": [{"line": #0, "column": #0}],
    "message": "Session token is invalid"
  }
}
```

