
# Websockets Documentation
This documentation contains how to connect to the WebSockets hosted by bubblez for getting post and reply data right after it has been posted.

## Connecting
To connect to the WebSocket, you can use one of two ways to connect.  
For live: wss://ws.bubblez.app:23831  
For canary: wss://ws.bubblez.app:23830  
The WebSocket expects all messages that are being sent to be JSON data.
The WebSocket also sends messages as JSON data.
If you send a message that is not properly encoded JSON data you will receive this message:
```JSON
{
    "message": "INVALID_JSON"
}
```

## Authentication
After connecting to the server you will receive this message:
```JSON
{
    "message": "AUTHENTICATION_REQUIRED"
}
```
When you receive this message the server is ready for you to be authenticated you need to send a message containing the following data and replace "token here" with your token.
```JSON
{
    "message": "SEND_TOKEN",
    "token": "token here"
}
```
After sending that message you should receive this message:
```JSON
{
    "message": "AUTHENTICATED",
    "heartbeatinterval": 40000
}
```
The heartbeatinterval can be different from the documentation, it is expected that you use the hearbeatinterval that the server gave you and not the amount that is listed here.  
If the token you provided is invalid you will receive this message:
```JSON
{
    "message": "INVALID_TOKEN"
}
```
You can reattempt authenticating if this happens, but before you reattempt double check your token.

## Heartbeats
When authenticating you receive a heartbeatinterval.  
The heartbeatinterval is the number of milliseconds between heartbeats.  
There is no need for sending heartbeats early due to ping or other issues that could slow the internet due to heartbeat checking which will be talked about later.  
When you need to send a heartbeat you need to send this data:
```JSON
{
    "message": "HEARTBEAT"
}
```
The WebSocket server will respond with:
```JSON
{
    "message": "HEARTBEAT_ACK"
}
```
If the WebSocket does not respond to heartbeats the connection can be considered zombified and it's recommended to terminate the connection and reconnect.

## Heartbeat checking
The server keeps track of heartbeats to also terminate zombified connections server side.  
You are allowed to not send any heartbeats for 1.5 times the heartbeatinterval.  
This is not recommended but would be possible.  
When you haven't sent a heartbeat in 1.5 times the heartbeatinterval the server will send the following message:
```JSON
{
    "message": "HEARTBEAT_MISSED",
    "heartbeatinterval": 40000
}
```
The heartbeatinterval can be different from the documentation, it is expected that you use the hearbeatinterval that the server gave you and not the amount that is listed here.  
When you receive this message you need to send a heartbeat right away no matter the time you would have left to send another heartbeat.  
The heartbeatinterval is also sent again and you're expected to restart the interval.  
If you fail to send a heartbeat within 2 times the heartbeatinterval the connection will be terminated because it's assumed that the connection has been zombified.

## New message
When a new message has been posted to bubblez a message will be sent containing the following data:
```JSON
{
    "message": "NEW_POST",
    "postdata": {
        
    }
}
```
Inside of postdata you will get the information you would receive from the api/v1/post/get api endpoint (Read the api documentation to see what information will be sent).

## New reply
When a new reply has been posted to bubblez a message will be sent containing the following data:
```JSON
{
    "message": "NEW_REPLY",
    "postdata": {
        
    },
    "replydata": {

    }
}
```
Inside of postdata you will get the information you would receive from the api/v1/post/get api endpoint (Read the api documentation to see what information will be sent).  
Inside of replydata you will get the information you would receive from the postdata and then read the reply from the replies data (api/v1/post/get -> replies -> the reply that has just been posted).

## New devlog
When a new devlog has been posted to bubblez a message will be sent containing the following data:
```JSON
{
    "message": "NEW_DEVLOG",
    "postdata": {
        
    }
}
```
Inside of postdata you will get the information you would receive from the api/v1/blog/latest api endpoint (Read the api documentation to see what information will be sent).  