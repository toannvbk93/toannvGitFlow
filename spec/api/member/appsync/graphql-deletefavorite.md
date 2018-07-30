# deleteFavorite

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /graphql | deleteFavorite | Graphql \(POST\) | Required |

Deletes a specific title from my list.

## Specification

### Request Query Schema

```text
mutation {
  deleteFavorite (bookId : “<Book ID>”)
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

| Success | Deletes a specific title from my list. |
| --- | --- |
| ErrorType | Authentication FailureSession token is invalidInternal Server ErrorInternal server error occured |

#### Success Schema

```text
{
  data : {
    deleteFavorite : {
      result : boolean,
      code : number,
      message : string
    }
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“deleteFavorite”],
    "data": { … },
    "errorType": "<Authentication Failure | Internal Server Error>",
    "locations": [{"line": #0, "column": #0}],
    "message": "<Session token is invalid | Internal server error occured >"
  }
}
```

## Sample

```text
{
  data: {
    deleteFavorite : {
      result : (true | false),
      code : 200, // identifier of cause
      message : “OK”, // message to the client.
    }
  }

  /* when the error occurs */
  error: {
    "path": [“deleteFavorite ”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

