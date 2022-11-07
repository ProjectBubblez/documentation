# Old API Documentation V2

* This page will be deleted if [Draft 3](api-1.md) goes well
* This is a list of all the current endpoints with updated methods and responses (after will be a list of new endpoints for v2)
* Draft 2
* `reason` can be left NULL if you don't want a reason to your actions

***

### Blogs

***

`GET` `/blog/latest`

request:

```
you don't need to send any data (this is a public endpoint)
```

response:

```json
{
	"error": false,
	"blog": {
		"content": "string",
		"image": "string",
		"tag": "string",
		"date": "integer"
	},
	"user": {
		"uuid": "string",
		"username": "string",
		"displayname": "string",
		"pfp": "string"
	}
}
```

***

### Posts

***

`DELETE` `/post/{post_id}`

request:

```json
{
	"token": "string",
	"reason": "string"
}
```

response:

```json
{
	"error": false,
	"post": {
		"id": "string",
	},
	"reason": "string"
}
```

***

`UPDATE` `/post/{post_id}`

request:

```json
{
	"token": "string",
	"content": "string",
	"lock": "boolean",
	"nsfw": "boolean",
	"reason": "string"
}
```

`NOTE`: `for content, lock and nsfw: if left as null, nothing will be updated`

response:

```json
{
	"error": false,
	"post": {
		"id": "string",
		"content": "string",
		"lock": "boolean",
		"nsfw": "boolean"
	},
	"reason": "string"
}
```

`NOTE1`: `if "true" post has been locked, if "false" post has been unlocked`\
`NOTE2`: `if "true" post has been set as nsfw, if "false" post has been unset as nsfw`

***

`GET` `/post/{post_id}`

request:

```json
{
	"token": "string"
}
```

response:

```json
{
	"error": false,
	"post": {
		"id": "string",
		"content": "string",
		"from": "string",
		"lock": "boolean",
		"nsfw": "boolean",
		"edited": "integer",
		"date": "integer",
		"replies": {
			"id": "string",
			"id": "string"
		}
	},
	"user": {
		"uuid": "string",
		"username": "string",
		"displayname": "string",
		"pfp": "string"
	}
}
```

***

`POST` `/post`

request:

```json
{
	"token": "string",
	"parent": "string",
	"content": "string",
	"from": "string",
	"lock": "boolean",
	"nsfw": "boolean"
}
```

`NOTE`: `for lock and nsfw: default "false"`

response:

```json
{
	"error": false,
	"post": {
		"id": "string",
		"parent_id": "string",
		"content": "string",
		"from": "string",
		"lock": "boolean",
		"nsfw": "boolean"
	}
}
```

`NOTE`: `you only need "parent_id" if you're replying to a post or another reply`

***

### Users

***

`GET` `/user`

request:

```json
{
	"token": "string",
	"username": "string",
	"uuid": "string"
}
```

`NOTE1`: `please only send "username" OR "uuid", if you send both it will return an error`\
`NOTE2`: `if both are null will send bot info`

response:

```json
{
	"error": false,
	"user": {
		"type": "integer",
		"uuid": "string",
		"username": "string",
		"displayname": "string",
		"banner": "string",
		"badge": "json",
		"special_badge": "json",
		"bio": "string",
		"nsfw": "boolean",
		"private": "boolean",
		"pronoun": "json",
		"joined": "integer"
	}
}
```

`NOTE1`: `type: 0 = User, 1 = Bot`\
`NOTE2`: `both nsfw and private will be "false" for bot accounts`\
`NOTE3`: `A way to get other bot info will come later`

***

`GET` `/ping`

request:

```json
{
	"token": "string"
}
```

response:

```json
{
	"error": false
}
```

`NOTE`: `This is used to tell if the site is online without a massive response back`

***

### NEW FOR V2

***

`UPDATE` `/profile`

request:

```json
{
	"token": "string",
	"username": "string",
	"displayname": "string",
	"pfp": "string",
	"banner": "string",
	"bio": "string"
}
```

`NOTE`: `Leave any null to leave them unchanged`

response:

```json
{
	"error": false,
	"updated": {
		"username": "string",
		"displayname": "string",
		"pfp": "string",
		"banner": "string",
		"bio": "string"
	}
}
```

`NOTE`: `Will return NULL if unchanged`

***
