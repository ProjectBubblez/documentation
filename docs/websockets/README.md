# WebSockets

This is the documentation for the bubblez websocket server.\
Here you will find everything you need to know to connect and authenticate to the websocket server, send heartbeats, receive data etc.

## Versions

The websocket server uses versions to not cause major downtime and give developers the chance to change their code when a major update happens.\
Below you can see a table of versions.

| Version     | Status       |
| ----------- | ------------ |
| [V1](V1.md) | Discontinued |
| [V0](V0.md) | Discontinued |

## General information

There is some general information which is the same in all different versions.\
Below you can see a table with a description and link to the documentation for this info.

| Name                                           | Description                                                                                                                                                                     |
| ---------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Close codes](CLOSECODES.md)                   | When something goes wrong while connected to the websocket you might be disconnected, the websocket will give you a close code which you can use to find out what the issue is. |
| [Connecting and authentication](CONNECTING.md) | To use the websocket server you need to first connect and be properly authenticated.                                                                                            |
| [Heartbeats](HEARTBEATS.md)                    | When the connection has been established you need to send heartbeats to make sure the connection hasn't been zombified.                                                         |
