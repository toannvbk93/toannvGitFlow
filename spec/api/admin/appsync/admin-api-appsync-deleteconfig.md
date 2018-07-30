# deleteConfig

## Overview

| Endpoint | Name | Type | Authentication |
| --- | --- | --- | --- |
| /graphql | deleteConfig | Graphql | Required |

Deletes system setting information.

## Specification

### Request Query Schema

```text
mutation {
  deleteConfig (configId: “<Config ID>”)
}
```

### Parameters

| Name | Type | Description |
| --- | --- | --- |
| configId | ID! | The identifier of Config. |

### Request Header

Must set token to ‘Authorization’ HTTP header.

ex\) Authorization: Bearer asdfasdfasdfasdfasdf

### Result

| Success | Return delete success information |
| --- | --- |
| ErrorType | Authentication FailureSession token is invalidInternal Server Error |

#### Success Schema

```text
{
  data : {
    deleteConfig : {
      result : (true | false),
      code : 200, // identifier of cause
      message : “OK”, // message to the client.
    }
  }
}
```

#### Error Schema

```text
{
  error: {
    "path": [“deleteConfig”],
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
    deleteConfig : {
      result : true,
      code : 200,
      message : “OK.”
    }
  }
  /* when the error occurs */
  error: {
    "path": [“deleteConfig”],
    "data": { … },
    "errorType": "...Exception",
    "locations": [{"line": #0, "column": #0}],
    "message": "..."
  }
}
```

