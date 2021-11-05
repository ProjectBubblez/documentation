# Close codes
When something went wrong with websocket communication the server can decide to close the connection.  
When a connection is closed there will be a code attached to it.  
If you receive a non 4000 error the connection was closed because of external reasons which should be reported to us.  
If you receive any of these codes you should investigate the reason of the error and fix it (with the exception of code 4000).  
Do not repeat sending messages before the issue has been resolved.

<table>
  <tr>
    <th>Close code</th>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>4000</td>
    <td>Unknown error</td>
    <td>Something unexpected happened. Try reconnecting.</td>
  </tr>
  <tr>
    <td>4001</td>
    <td>Invalid JSON</td>
    <td>Invalid JSON has been received. Check syntax before trying again.</td>
  </tr>
  <tr>
    <td>4002</td>
    <td>Not authenticated</td>
    <td>You tried sending a request without being authenticated.</td>
  </tr>
  <tr>
    <td>4003</td>
    <td>Authentication failed</td>
    <td>We were unable to authenticate you with the token we received.</td>
  </tr>
  <tr>
    <td>4004</td>
    <td>Bad request</td>
    <td>We received invalid information or information is missing.</td>
  </tr>
</table>
  
Go back to the [readme](https://github.com/ProjectBubblez/documentation/blob/main/docs/websockets/README.md)