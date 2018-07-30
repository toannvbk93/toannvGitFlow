# admin/login

## Overview

| Endpoint | Name | Type |
| --- | --- | --- |
| /admin/login | login \(Administrator\) | POST |

Logs in to the store API server and generates a session.

## Specification

### Parameters

| Name | Type | Req. | Description |
| --- | --- | --- | --- |
| userId | String! | \* | The identifier of administrator user. |
| password | String! | \* | password |

### Request

useId, password as POST Parameters

### Response

| Success | Redirect to “/admin” |
| --- | --- |
| Error | Return to &lt;TBD&gt; |

