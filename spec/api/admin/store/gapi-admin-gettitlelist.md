# admin/getTitleList

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /gapi/admin | getTitleList | Graphql(POST) | Required |

Retrieves a list of titles under specified conditions.

## Specification

### Request Query Schema

```text
query {
  getTitleList (
    keyword : “<keyword>”
    ,dcCategory: “<DC Category ID>”
    ,storeCategory: “<Store Category ID>”
    ,limit: <number> 
    ,pageToken:”<pageToken>” 
    ,sortkey : <new | title>
  )
}
```

### Parameters

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| keyword | String! | - | Search keyword for title |
| dcCategory | ID | - | The identifier of DC Category. |
| storeCategory | ID | - | The identifier of Store Category. |
| limit | Number | 10 | Maximum size of list items to get per query. |
| pageToken | String | - | The token to next page |
| sortKey | String | "new" | The name of the item to be sorted. Ascending order by the value of this key. |
|  |  |  |  |

### Request Header

Must set token to ‘Authorization’ HTTP header.
ex) Authorization: Bearer asdfasdfasdfasdfasdf.

### Result

<table>
<tr>
  <td>Success</td>
  <td><ul><li>Retrieves a list of titles under specified conditions.</li></ul></td>
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
    getTitleList : {
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
    "path": [“getTitleList”],
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
    getTitleList : {
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
    "path": [“getTitleList”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

