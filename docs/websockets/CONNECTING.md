# CONNECTING

## Connecting

To connect to the WebSocket, you can use one of two urls to connect.\
For live: ~~wss://ws.bubblez.app:23831~~ Discontinued\
For canary: ~~wss://ws.bubblez.app:23830~~ Discontinued\
The WebSocket expects all messages that are being sent to be JSON data.\
The WebSocket also sends messages as JSON data.\
Sending incorrect JSON data will result in the connection being [closed](CLOSECODES.md).

## Authentication

After connecting to the server you will receive this message:

```
{
    "message": "AUTHENTICATION_REQUIRED"
}
```

When you receive this message the server is ready for you to be authenticated you need to send a message containing the following data and replace "token here" with your token.

```
{
    "message": "SEND_TOKEN",
    "token": "token here",
    "version": 1
}
```

The version variable can be different based on the version you want to use.\
After sending that message you should receive this message:

```
{
    "message": "AUTHENTICATED",
    "heartbeatinterval": 40000
}
```

The heartbeatinterval can be different from the documentation, it is expected that you use the hearbeatinterval that the server gave you and not the amount that is listed here.\
If you provided an incorrect token the connection will be [closed](CLOSECODES.md).

Go back to the [readme](./)
