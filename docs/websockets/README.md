# Websockets
This is the documentation for the bubblez websocket server.  
Here you will find everything you need to know to connect and authenticate to the websocket server, send heartbeats, receive data etc.

## Versions
The websocket server uses versions to not cause major downtime and give developers the chance to change their code when a major update happens.  
Below you can see a table of versions.
<table>
  <tr>
    <th>Version</th>
    <th>Status</th>
  </tr>
  <tr>
    <td><a href="https://github.com/ProjectBubblez/documentation/blob/main/docs/websockets/V1.md">V1</a></td>
    <td>Available</td>
  </tr>
  <tr>
    <td><a href="https://github.com/ProjectBubblez/documentation/blob/main/docs/websockets/V0.md">V0</a></td>
    <td>Deprecated</td>
  </tr>
</table>

## General information
There is some general information which is the same in all different versions.  
Below you can see a table with a description and link to the documentation for this info.

<table>
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td><a href="https://github.com/ProjectBubblez/documentation/blob/main/docs/websockets/CLOSECODES.md">Close codes</a></td>
    <td>When something goes wrong while connected to the websocket you might be disconnected, the websocket will give you a close code which you can use to find out what the issue is.</td>
  </tr>
  <tr>
    <td><a href="https://github.com/ProjectBubblez/documentation/blob/main/docs/websockets/CONNECTING.md">Connecting and authentication</a></td>
    <td>To use the websocket server you need to first connect and be properly authenticated.</td>
  </tr>
  <tr>
    <td><a href="https://github.com/ProjectBubblez/documentation/blob/main/docs/websockets/HEARTBEATS.md">Heartbeats</a></td>
    <td>When the connection has been established you need to send heartbeats to make sure the connection hasn't been zombified.</td>
  </tr>
</table>