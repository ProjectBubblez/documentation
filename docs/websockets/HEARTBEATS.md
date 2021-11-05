# Heartbeats
When authenticating you will receive a heartbeatinterval.  
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

# Heartbeat checking
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
  
Go back to the [readme](https://github.com/ProjectBubblez/documentation/blob/main/docs/websockets/README.md)