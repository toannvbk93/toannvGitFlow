# Errortype List

<table>
<tr>
  <th>#</t>
  <th>ErrorType</th>
  <th>Message</th>
  <th>Description</th>
</tr>

<tr>
  <td>1</td>
  <td rowspan="4">AuthenticationFailureError</td>
  <td>Session token is invalid.</td>
  <td>Indicates that the session token check has failed.</td>
</tr>

<tr>
  <td>2</td>
  <td>T-Magazine Authentication error occured.</td>
  <td>Indicates that the authentication on the T-Magazine side has failed.</td>
</tr>  

<tr>
  <td>3</td>
  <td>Administrator Authentication error occured.</td>
  <td>Indicates that the authentication of the administrator function has failed.</td>
</tr>

<tr>
  <td>4</td>
  <td>Publisher Authentication error occured.</td>
  <td>Indicates that the authentication of the publisher API has failed.</td>
</tr>

<tr>
  <td>5</td>
  <td>AuthorityError</td>
  <td>Current user cannot use this function.</td>
  <td>Indicates that the user has accessed an API that can not be used with the current admin user's permissions.</td>
</tr>

<tr>
  <td>6</td>
  <td rowspan="4">InvalidArgumentError</td>
  <td>Page token is invalid.</td>
  <td>Indicates that the specified page token is invalid or incorrect.</td>
</tr>

<tr>
  <td>7</td>
  <td>Object id is not found.</td>
  <td>Indicates that there is no data corresponding to the specified object ID.</td>
</tr>  

<tr>
  <td>8</td>
  <td>Book download information is empty.</td>
  <td>Indicates that the download information attached to the book does not exist(cannot be retrieved from the publisher).</td>
</tr>

<tr>
  <td>9</td>
  <td>Input data is invalid.</td>
  <td>Indicates that an error has occurred in the input check other than the data type check</td>
</tr>

<tr>
  <td>10</td>
  <td>InternalServerError</td>
  <td>Internal server error occured.</td>
  <td>Indicates that an error which is not expected in API specifications has occurred. (Communication error, DB error, etc.)</td>
</tr>
</table>
