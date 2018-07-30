# Errotype List

| \# | ErrorType | Message | Description |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | AuthenticationFailureError | Session token is invalid. | Indicates that the session token check has failed. |
| 2 | T-Magazine Authentication error occured. | Indicates that the authentication on the T-Magazine side has failed. |  |
| 3 | Administrator Authentication error occured. | Indicates that the authentication of the administrator function has failed. |  |
| 4 | Publisher Authentication error occured. | Indicates that the authentication of the publisher API has failed. |  |
| 5 | AuthorityError | Current user cannot use this function. | Indicates that the user has accessed an API that can not be used with the current admin user's permissions. |
| 6 | InvalidArgumentError | Page token is invalid. | Indicates that the specified page token is invalid or incorrect. |
| 7 | Object id is not found. | Indicates that there is no data corresponding to the specified object ID. |  |
| 8 | Book download information is empty. | Indicates that the download information attached to the book does not exist\(cannot be retrieved from the publisher\). |  |
| 9 | Input data is invalid. | Indicates that an error has occurred in the input check other than the data type check |  |
| 10 | InternalServerError | Internal server error occured. | Indicates that an error which is not expected in API specifications has occurred. \(Communication error, DB error, etc.\) |

