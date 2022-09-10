# API Documentation V2
- This is a list of all the current endpoints with updated methods and responses (after will be a list of new endpoints for v2)
- Draft 1

----------------------------------------------------------------------------------
### Blogs
----------------------------------------------------------------------------------

`GET` `/blog/latest`

request:
```
you don't need to send any data (this is a public endpoint)
```

response:
```json
{
	'code': 200,
	'blog_id': "string",
	'blog_username': "string",
	'blog_displayname': "string",
	'blog_pfp': "string",
	'blog_content': "string",
	'blog_image': "string",
	'blog_tag': "string",
	'blog_date': "integer"
}
```

----------------------------------------------------------------------------------
### Posts
----------------------------------------------------------------------------------

`DELETE` `/post/{post_id}`

request:
```json
{
	'token': "string",
	'reason': "string" (can be left as null)
}
```

response:
```json
{
	'code': 200,
	'delete_post_id': "string",
	'delete_post_reason': "string"
}
```

----------------------------------------------------------------------------------

`PATCH` `/post/{post_id}`

request:
```json
{
	'token': "string",
	'content': "string", (if left as null, nothing will be updated)
	'lock': "boolean", (if left as null, nothing will be updated)
	'nsfw': "boolean", (if left as null, nothing will be updated)
	'reason': "string" (can be left as null)
}
```

response:
```json
{
	'code': 200,
	'update_post_id': "string",
	'update_post_content': "string",
	'update_post_lock': "boolean", (if "true" post has been locked, if "false" post has been unlocked)
	'update_post_nsfw': "boolean", (if "true" post has been set as nsfw, if "false" post has been unset as nsfw)
	'update_post_reason': "string"
}
```

----------------------------------------------------------------------------------

`GET` `/post/{post_id}`

request:
```json
{
	'token': "string"
}
```

response:
```json
{
	'code': 200,
	'post_id': "string",
	'post_username': "string",
	'post_displayname': "string",
	'post_pfp': "string",
	'post_content': "string",
	'post_from': "string",
	'post_lock': "boolean",
	'post_nsfw': "boolean",
	'post_edited': "integer",
	'post_date': "integer",
	'post_replies': {
		'post_reply_id': "integer",
		'post_reply_id': "integer"
	}
}
```

----------------------------------------------------------------------------------

`POST` `/post`

request:
```json
{
	'token': "string",
	'content': "string",
	'from': "string",
	'lock': "boolean", (default "false")
	'nsfw': "boolean" (default "false")
}
```

response:
```json
{
	'code': 200,
	'post_id': "string",
	'post_content': "string",
	'post_from': "string",
	'post_lock': "boolean",
	'post_nsfw': "boolean"
}
```

----------------------------------------------------------------------------------
### Replies
----------------------------------------------------------------------------------

`DELETE` `/reply/{reply_id}`

request:
```json
{
	'token': "string",
	'reason': "string" (can be left as null)
}
```

response:
```json
{
	'code': 200,
	'delete_reply_id': "string",
	'delete_reply_reason': "string"
}
```

----------------------------------------------------------------------------------

`PATCH` `/reply/{reply_id}`

request:
```json
{
	'token': "string",
	'content': "string", (if left as null, nothing will be updated)
	'lock': "boolean", (if left as null, nothing will be updated)
	'nsfw': "boolean", (if left as null, nothing will be updated)
	'reason': "string" (can be left as null)
}
```

response:
```json
{
	'code': 200,
	'update_reply_id': "string",
	'update_reply_content': "string",
	'update_reply_lock': "boolean", (if "true" reply has been locked, if "false" reply has been unlocked)
	'update_reply_nsfw': "boolean", (if "true" reply has been set as nsfw, if "false" reply has been unset as nsfw)
	'update_reply_reason': "string"
}
```

----------------------------------------------------------------------------------

`POST` `/reply/{p OR r}/{post/reply_id}`

request:
```json
{
	'token': "string",
	'id': "string",
	'content': "string",
	'from': "string",
	'lock': "boolean", (default "false")
	'nsfw': "boolean" (default "false")
}
```

response:
```json
{
	'code': 200,
	'reply_post_id': "string" OR 'reply_reply_id': "string",
	'reply_id': "string",
	'reply_content': "string",
	'reply_from': "string",
	'reply_lock': "boolean",
	'reply_nsfw': "boolean"
}
```

`NOTE`: `I understand this one might be confusing but more will be explained later`

----------------------------------------------------------------------------------
### Users
----------------------------------------------------------------------------------

`GET` `/user`

request:
```json
{
	'token': "string",
	'username': "string" || 'uuid': "string" (should only send one will return error if both are sent. if both are null will send bot info)
}
```

response:
```json
{
	'code': 200,
	'user_bot': "boolean", (FALSE FOR USERS)
	'user_uuid': "string",
	'user_username': "string",
	'user_displayname': "string",
	'user_banner': "string",
	'user_badge': "json",
	'user_special_badge': "json",
	'user_bio': "string",
	'user_nsfw': "boolean", (NULL FOR BOTS)
	'user_private': "boolean", (NULL FOR BOTS)
	'user_pronoun': "json",
	'user_joined': "integer"
}
```

`NOTE`: `A way to get other bot info will come later`

----------------------------------------------------------------------------------

`GET` `/ping`

request:
```json
{
	'token': "string"
}
```

response:
```json
{
	'code': 200
}
```

`NOTE`: `This is used to tell if the site is online without a massive response back`

----------------------------------------------------------------------------------
### NEW FOR V2
----------------------------------------------------------------------------------

`PATCH` `/update`

request:
```json
{
	'token': "string",
	'username': "string",
	'displayname': "string",
	'pfp': "string",
	'banner': "string",
	'bio': "string"
}
```

`NOTE`: `Leave any null to leave them unchanged`

response:
```json
{
	'code': 200,
	'updated_username': "string",
	'updated_displayname': "string",
	'updated_pfp': "string",
	'updated_banner': "string",
	'updated_bio': "string"
}
```

`NOTE`: `Will return NULL if unchanged`

----------------------------------------------------------------------------------