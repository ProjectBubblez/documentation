
# API Documentation
This documentation contains everything you need to know about the official bubblez api.

## URLS
You must re
For live: https://bubblez.app/api/v1  
For canary: Dead

## Requests

## Blogs

`POST` /blog/latest  
`token` - api token for settings  

receive:
```json
{
    "200": "latest Blog Post",
    "blogid": "",
    "blogposter_username": "",
    "blogposter_displayname": "",
    "blogposter_pfp": "",
    "blogcontent": "",
    "blogdate": "1990-01-01 00:00:00"
}
```

## Posts

`POST` /post/send  
`token` - api token for settings  
`post` - the message you want the post to contain  
`from` - the little message next to the post date  
`locked` - accepts value `true` defaults to false  
`nsfw` - accepts value `true` defaults to false  

receive:
```json
{
    "200": "message sent",
    "post": "API is cool",
    "from": "API testing",
    "locked": "false",
    "pnsfw": "false",
    "postid": 522
}
```

`POST` /post/lock  
`token` - api token for settings  
`postid` - the id of the post you want to lock or unlock  
`togglelock` - accepted values `true` or `false`  

receive:
```json
{
    "200": "Post 522 has been locked"
}
```
```json
{
    "200": "Post 522 has been unlocked"
}
```

`POST` /post/delete  
`token` - api token for settings  
`postid` - the id of the post you wish to delete  
`confirm` - accepted value `true` anything else will cancel the request  

receive:
```json
{
    "200": "Post 522 has been deleted"
}
```

`POST` /post/get  
`token` - api token for settings  
`postid` - the id of the post you wish to collect info on  

receive:
```json
{
    "200": "Found post",
    "postid": "522",
    "username": "DarkMatter",
    "pfp": "https://i.imgur.com/jAOd5gE.png",
    "nsfw": "false",
    "content": "API is cool",
    "from": "API testing",
    "locked": "false",
    "edited": null,
    "post_date": "2021-07-30 12:18:31",
    "replies": [
        {
            "replyid": "1473",
            "username": "DarkMatter",
            "pfp": "https://i.imgur.com/jAOd5gE.png",
            "content": "Cool reply with the API",
            "from": null,
            "deleted": null,
            "edit_date": null,
            "reply_date": "2021-07-30 12:49:12"
        }
    ]
}
```

`POST` /post/latest  
`token` - api token for settings  

receive:
```json
{
    "200": "latest Post",
    "postid": "522"
}
```

`POST` /post/edit  
`token` - api token for settings  
`postid` - the id of the post you want to edit  
`post` - the message you want to change your post to  

```json
{
    "200": "Post 522 has been updated"
}
```

## Replies

`POST` /reply/send  
`token` - api token for settings  
`postid` - the id of the post you want to reply to  
`reply` - the message you want the reply to contain  
`from` - the little message next to the reply date  
`nsfw` - accepts value `true` defaults to false  

receive:
```json
{
    "200": "reply sent",
    "reply": "Cool reply with the API",
    "postid": "522",
    "from": "API testing",
    "rnsfw": "false",
    "replyid": 1473
}
```

`POST` /reply/delete  
`token` - api token for settings  
`replyid` - the id of the reply you wish to delete  
`confirm` - accepted value `true` anything else will cancel the request  

receive:
```json
{
    "200": "reply 1473 has been deleted"
}
```

`POST` /reply/edit  
`token` - api token for settings  
`replyid` - the id of the reply you want to edit  
`reply` - the message you want to change your reply to  

```json
{
    "200": "Reply 1473 has been updated"
}
```


## Users

`POST` /user/check  
`token` - api token for settings  

receive:
```json
{
    "200": "Found user",
    "uuid": null,
    "username": "DarkMatter",
    "displayname": "DarkMatter",
    "email": null,
    "pfp": "https://i.imgur.com/jAOd5gE.png",
    "banner": "https://i.imgur.com/1bZdeBF.png",
    "coins": "85",
    "rank": "founder",
    "eventr": "darkmatter",
    "patreon": "true",
    "booster": "true",
    "bio": "We don't know much about them, but we're sure DarkMatter is great.",
    "nsfw": "false",
    "dob": null,
    "pronoun": "hehim",
    "ban": null,
    "created_at": "2019-10-21 07:40:23",
    "last_posted": "2021-07-30 01:19:36",
    "posts": [
        {
            "postid": "522",
            "username": "DarkMatter",
            "nsfw": "false",
            "content": "API is cool",
            "from": "API testing",
            "locked": "false",
            "edited": null,
            "post_date": "2021-07-30 12:18:31"
        }
    ],
    "replies": [
        {
            "replyid": "1473",
            "postid": "522",
            "username": "DarkMatter",
            "nsfw": "false",
            "content": "Cool reply with the API",
            "from": "API testing",
            "edited": null,
            "reply_date": "2021-07-30 12:49:12"
        }
    ]
}
```

`NOTE: UUID will not be null on the main site, we're just showing examples from canary`

`POST` /user/get  
`token` - api token for settings  
`username` - the bubblez username of the user you want to grab info from  

receive:

```json
{
    "200": "Found user",
    "uuid": null,
    "username": "embed",
    "displayname": "embed",
    "followers": 2,
    "pfp": "https://i.imgur.com/Md5C3uy.gif",
    "banner": null,
    "coins": "0",
    "rank": "founder",
    "eventr": "lgbt19",
    "patreon": "true",
    "booster": "true",
    "bio": "the best bubblez dev.",
    "nsfw": "false",
    "pronoun": "none",
    "ban": null,
    "created_at": "2019-10-22 12:04:01",
    "last_posted": null,
    "posts": [
        {
            "postid": "280",
            "username": "embed",
            "nsfw": "false",
            "content": "gamimg",
            "from": null,
            "locked": "false",
            "edited": null,
            "post_date": "2020-08-09 17:15:19"
        }
    ]
}
```

`POST` /user/ping  
`token` - api token for settings  

receive:
```json
{
    "200": "Pong",
    "username": "DarkMatter",
    "online_status": "2021-07-30 13:03:18"
}
```
