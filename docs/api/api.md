
# API Documentation V1
This documentation contains everything you need to know about the official bubblez api.

## URLS
You must apply for a token at https://bubblez.app/applications/api-token  
For live: https://bubblez.app/api/v1  
For canary: Depricated

## Requests

## Blogs

`POST` /blog/latest  

receive:
```json
{
    "200": "latest Blog Post",
    "blogid": "",
    "blogposter_username": "",
    "blogposter_displayname": "",
    "blogposter_pfp": "",
    "blogcontent": "",
    "blogimage": "",
    "blogtag": "",
    "blogdate": "1990-01-01 00:00:00"
}
```

## Posts

`POST` /post/send  
`token` - api token from settings  
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
`token` - api token from settings  
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
`token` - api token from settings  
`postid` - the id of the post you wish to delete  
`confirm` - accepted value `true` anything else will cancel the request  

receive:
```json
{
    "200": "Post 522 has been deleted"
}
```

`POST` /post/get  
`token` - api token from settings  
`postid` - the id of the post you wish to collect info on  

receive:
```json
{
    "200": "Found post",
    "postid": "522",
    "username": "DarkMatter",
    "pfp": "https://cds.bubblez.app/v2/get/bblz_606df5400f64a/display",
    "content": "API is cool",
    "from": "API testing",
    "locked": "false",
    "pnsfw": "false",
    "edited": null,
    "post_date": "2021-07-30 12:18:31",
    "replies": [
        {
            "replyid": "1473",
            "username": "DarkMatter",
            "pfp": "https://cds.bubblez.app/v2/get/bblz_606df5400f64a/display",
            "content": "Cool reply with the API",
            "from": null,
            "rnsfw": "false",
            "deleted": null,
            "edit_date": null,
            "reply_date": "2021-07-30 12:49:12"
        }
    ]
}
```

`POST` /post/latest  
`token` - api token from settings  

receive:
```json
{
    "200": "latest Post",
    "postid": "522"
}
```

`POST` /post/edit  
`token` - api token from settings  
`postid` - the id of the post you want to edit  
`post` - the message you want to change your post to  

```json
{
    "200": "Post 522 has been updated"
}
```

## Replies

`POST` /reply/send  
`token` - api token from settings  
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
`token` - api token from settings  
`replyid` - the id of the reply you wish to delete  
`confirm` - accepted value `true` anything else will cancel the request  

receive:
```json
{
    "200": "reply 1473 has been deleted"
}
```

`POST` /reply/edit  
`token` - api token from settings  
`replyid` - the id of the reply you want to edit  
`reply` - the message you want to change your reply to  

```json
{
    "200": "Reply 1473 has been updated"
}
```


## Users

`POST` /user/check  
`token` - api token from settings  

receive:
```json
{
    "200": "Found user",
    "uuid": "bblz_606df5400f64a",
    "username": "Zak",
    "displayname": "Zak",
    "email": null,
    "pfp": "https://cds.bubblez.app/v2/get/bblz_606df5400f64a/display",
    "banner": "https://cds.bubblez.app/v2/get/bblz_606df5400f64a/banner",
    "coins": "865",
    "rank": "[\"founder\", \"verified\"]",
    "badges": "[\"lgbt22\", \"alpha\", \"private\"]",
    "bio": "Just doing internet things\r\n\r\nbblz_606df56eeb955 CEO",
    "nsfw": "false",
    "dob": null,
    "pronoun": "hehim",
    "ban": null,
    "created_at": "2019-10-21 07:40:23",
    "last_posted": "2022-10-09 14:25:22",
    "posts": [
        {
            "postid": "522",
            "username": "Zak",
            "content": "API is cool",
            "from": "API testing",
            "locked": "false",
            "pnsfw": "false",
            "edited": null,
            "post_date": "2021-07-30 12:18:31"
        }
    ],
    "replies": [
        {
            "replyid": "1473",
            "postid": "522",
            "username": "Zak",
            "content": "Cool reply with the API",
            "from": "API testing",
            "rnsfw": "false",
            "edited": null,
            "reply_date": "2021-07-30 12:49:12"
        }
    ]
}
```

`POST` /user/get  
`token` - api token from settings  
`username` - the bubblez username of the user you want to grab info from  

receive:

```json
{
    "200": "Found user",
    "uuid": "bblz_606df56f4d112",
    "username": "embed",
    "displayname": "embed",
    "followers": 26,
    "pfp": "https://cds.bubblez.app/v2/get/bblz_606df56f4d112/display",
    "banner": "https://cds.bubblez.app/v2/get/bblz_606df56f4d112/banner",
    "coins": "74",
    "rank": "[\"founder\", \"verified\"]",
    "badges": "[\"lgbt19\", \"alpha\", \"private\"]",
    "bio": "the best founder (tbh)\r\nhttps://astolfo.co\r\n\r\nposts made here are of my own opinion and do not represent the views of Bubblez as a company.",
    "nsfw": "false",
    "pronoun": "hehim",
    "ban": null,
    "created_at": "2019-10-22 12:04:01",
    "last_posted": null,
    "posts": [
        {
            "postid": "280",
            "username": "embed",
            "content": "gaming",
            "from": null,
            "locked": "false",
            "pnsfw": "false",
            "edited": null,
            "post_date": "2020-08-09 17:15:19"
        }
    ]
}
```

`POST` /user/ping  
`token` - api token from settings  

receive:
```json
{
    "200": "Pong",
    "username": "Zak",
    "online_status": "2021-07-30 13:03:18"
}
```
