API_REST.md   

# Rocket.Chat APIs test

## Insomnia - API Design Platform and API Client
Install insomnia to start create the API REST.
```
$sudo snap install insomnia
$insomnia
```
# Info
## [/api/info](http://localhost:3000/api/info)
Run the info call to confirm if the server is working.

``` json
{ 
    "url": "http://localhost:3000/api/info",
    "name": "Info",
    "description": "",
    "method": "GET",
 }
```
## Result

``` json
{ 
    "version": "3.13.2",
    "success": true
 }
```

# Login
## [/api/v1/login](http://localhost:3000/api/v1/login)
Proceed with login, just to ensure the authentication

## Payload
``` json
{
    "url": "http://localhost:3000/api/v1/login",
    "name": "Auth",
    "description": "",
    "method": "POST",
    "body": {
        "mimeType": "application/json",
        "text": "{\n  \"user\": \"phpilatti@gmail.com\",\n  \"password\": \"pedroteste\"\n}"
}
```
## header
``` json 
"headers": [
    {
        "name": "Content-Type",
        "value": "application/json",
        "id": "pair_5807f9ae3fd6437591784ca8a828d193"
     }
```
## Result
```json
[02:24, 17/04/2021] Pedro Pilatti: {
  "status": "success",
  "data": {
    "userId": "NenatsjtsGG37mYj2",
    "authToken": "7nGNatj2uj2LDGm9Etd3JitgowoAGigZenSPoCn6jFu",
    "me": {
      "_id": "NenatsjtsGG37mYj2",
      "services": {
        "password": {
          "bcrypt": "$2b$10$m9BXr5iXpBfUX2G8.JofBef3nnjOepvYy5wANwpFoojPMtoZkJQSm"
        },
        "email2fa": {
          "enabled": true
        }
      },
      "emails": [
        {
          "address": "phpilatti@gmail.com",
          "verified": false
        }
      ],
      "status": "online",
      "active": true,
      "_updatedAt": "2021-04-16T04:07:43.191Z",
      "roles": [
        "admin"
      ],
      "name": "Pedro Pilatti",
      "statusConnection": "online",
      "username": "Pilatti",
      "utcOffset": -3,
      "avatarUrl": "http://localhost/avatar/Pilatti",
      "settings": {
        "preferences": {
          "enableAutoAway": true,
          "idleTimeLimit": 300,
          "desktopNotificationRequireInteraction": false,
          "audioNotifications": "mentions",
          "desktopNotifications": "all",
          "mobileNotifications": "all",
          "unreadAlert": true,
          "useEmojis": true,
          "convertAsciiEmoji": true,
          "autoImageLoad": true,
          "saveMobileBandwidth": true,
          "collapseMediaByDefault": false,
          "hideUsernames": false,
          "hideRoles": false,
          "hideFlexTab": false,
          "hideAvatars": false,
          "sidebarGroupByType": true,
          "sidebarViewMode": "medium",
          "sidebarHideAvatar": false,
          "sidebarShowUnread": false,
          "sidebarSortby": "activity",
          "showMessageInMainThread": false,
          "sidebarShowFavorites": true,
          "sendOnEnter": "normal",
          "messageViewMode": 0,
          "emailNotificationMode": "mentions",
          "newRoomNotification": "door",
          "newMessageNotification": "chime",
          "muteFocusedConversations": true,
          "notificationsSoundVolume": 100,
          "sidebarShowDiscussion": true
        }
      }
    }
  }
}
```

## 1.	Create a new user via an API endpoint

## [/api/v1/users.create](http://localhost:3000/api/v1/users.create)   

## Payload
```json
{
    "url": "http://localhost:3000/api/v1/users.create",
    "name": "CreateUser",
    "description": "",
    "method": "POST",
    "body": {
        "mimeType": "application/json",
        "text": "{\t\n\t\"email\": \"rocketchat@rocket.com\",\n\t\"name\": \"Rocket Chat\",\n\t\"password\": \"Rocket\",\n\t\"username\": \"RocketChat\"\n}"
 }
```
## Header
Using information returned in Login
```json
 "headers": 
{
    "name": "Content-Type",
    "value": "application/json"
},
{
    "name": "X-Auth-Token",
    "value": "7nGNatj2uj2LDGm9Etd3JitgowoAGigZenSPoCn6jFu"
},
{
    "name": "X-User-Id",
    "value": "NenatsjtsGG37mYj2"
}
```
## Result
```json
{
  "user": {
    "_id": "woKEsunYs58yLJCYM",
    "createdAt": "2021-04-17T02:40:11.283Z",
    "username": "RocketChat",
    "emails": [
      {
        "address": "rocketchat@rocket.com",
        "verified": false
      }
    ],
    "type": "user",
    "status": "offline",
    "active": true,
    "_updatedAt": "2021-04-17T02:40:12.732Z",
    "__rooms": [
      "GENERAL"
    ],
    "roles": [
      "user"
    ],
    "name": "Rocket Chat",
    "settings": {}
  },
  "success": true
}
```

## 2.	Get the room information via an API endpoint
## [/api/v1/rooms.info](http://localhost:3000/api/v1/rooms.info)
## Query Parameters
```json
{
    "url": "http://localhost:3000/api/v1/rooms.info",
    "name": "RoomInfo",
    "description": "",
    "method": "GET",
    "body": {},
    "parameters": [
        {
            "name": "roomId",
            "value": "GENERAL",
            "description": "",
            "id": "pair_994145c5818941dbb540b1baec2a7e6c"
        },
        {
            "name": "roomName",
            "value": "general",
            "description": "",
            "id": "pair_ff48693ee1304677a7b3f0681cd270f4"
        }
```

## Header
Using information returned in Login
```json
 "headers": 
{
    "name": "Content-Type",
    "value": "application/json"
},
{
    "name": "X-Auth-Token",
    "value": "7nGNatj2uj2LDGm9Etd3JitgowoAGigZenSPoCn6jFu"
},
{
    "name": "X-User-Id",
    "value": "NenatsjtsGG37mYj2"
}
```
## Result
```json
{
  "room": {
    "_id": "GENERAL",
    "ts": "2021-04-16T01:36:05.284Z",
    "t": "c",
    "name": "general",
    "usernames": [],
    "msgs": 6,
    "usersCount": 3,
    "default": true,
    "_updatedAt": "2021-04-16T04:08:55.017Z",
    "lastMessage": {
      "rid": "GENERAL",
      "msg": "alo",
      "ts": "2021-04-16T03:02:40.413Z",
      "u": {
        "_id": "NenatsjtsGG37mYj2",
        "username": "Pilatti"
      },
      "mentions": [],
      "channels": [],
      "_updatedAt": "2021-04-16T03:02:40.437Z",
      "_id": "79BarKDyY3na5WzP6"
    },
    "lm": "2021-04-16T03:02:40.413Z"
  },
  "success": true
}
```

## 3.	Get a list of all user roles in the system via an API endpoint
## [/api/v1/users.list](http://localhost:3000/api/v1/users.list)
## Query Parameters Optional
```json
{
    "url": "http://localhost:3000/api/v1/users.list",
    "name": "UsersList",
    "description": "",
    "method": "GET",
}
```
## Header
Using information returned in Login
```json
 "headers": 
{
    "name": "Content-Type",
    "value": "application/json"
},
{
    "name": "X-Auth-Token",
    "value": "7nGNatj2uj2LDGm9Etd3JitgowoAGigZenSPoCn6jFu"
},
{
    "name": "X-User-Id",
    "value": "NenatsjtsGG37mYj2"
}
```
## Result
```json
{
  "users": [
    {
      "_id": "XfpfCGG957zam9pH5",
      "username": "Carol",
      "emails": [
        {
          "address": "carolini@gmail.com",
          "verified": false
        }
      ],
      "status": "offline",
      "active": true,
      "roles": [
        "leader"
      ],
      "name": "Carolini Willers",
      "nameInsensitive": "carolini willers"
    },
    {
      "_id": "wjxtkj5aGZq3juEmu",
      "username": "JSAK",
      "emails": [
        {
          "address": "jonas@gmail.com",
          "verified": false
        }
      ],
      "status": "offline",
      "active": true,
      "roles": [
        "user"
      ],
      "name": "Jonas dos Santos",
      "nameInsensitive": "jonas dos santos"
    },
    {
      "_id": "NenatsjtsGG37mYj2",
      "emails": [
        {
          "address": "phpilatti@gmail.com",
          "verified": false
        }
      ],
      "status": "online",
      "active": true,
      "roles": [
        "admin"
      ],
      "name": "Pedro Pilatti",
      "username": "Pilatti",
      "nameInsensitive": "pedro pilatti"
    },
    {
      "_id": "woKEsunYs58yLJCYM",
      "username": "RocketChat",
      "emails": [
        {
          "address": "rocketchat@rocket.com",
          "verified": false
        }
      ],
      "status": "offline",
      "active": true,
      "roles": [
        "admin"
      ],
      "name": "Rocket Chat",
      "nameInsensitive": "rocket chat"
    },
    {
      "_id": "rocket.cat",
      "name": "Rocket.Cat",
      "username": "rocket.cat",
      "status": "online",
      "active": true,
      "roles": [
        "bot"
      ],
      "avatarETag": null,
      "nameInsensitive": "rocket.cat"
    }
  ],
  "count": 5,
  "offset": 0,
  "total": 5,
  "success": true
}
```
