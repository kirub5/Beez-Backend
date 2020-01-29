## Ask for Password-Reset

* Is used to change a forgotten password
* The request will send a token to the email, which will be used to reset the password
* ENDPOINT:- `POST` **/authmanagement**

#### Request:-
```
{
  "action": "sendResetPwd", // default
  "value": 
	{ 
    	"email": "user3@beez.com"   // email address of the user
	}
}
```
#### Response:-

* user object will be returned
```
{
    "_id": "5e31522aa52a1a023f3cda37",
    "activeConversationsIds": [],
    "cardsIds": [],
    "language": "en",
    "rolesIds": [
        "5e31522aa52a1a023f3cda38"
    ],
    "organizations": [
        "5e2eb10fc94f9d002f05a9a5"
    ],
    "accounts": [
        "5e2ecb776c8f6f01c905c16b"
    ],
    "accountModules": [],
    "email": "user3@beez.com",
    "isVerified": true,
    "createdAt": "2020-01-29T09:36:42.495Z",
    "updatedAt": "2020-01-29T09:36:42.548Z",
    "__v": 0,
    "beezInToAccount": "5e2ecb776c8f6f01c905c16b",
    "beezInToOrganization": "5e2eb10fc94f9d002f05a9a5"
}
```



## Reset the password

* Is used to actually change the password
* ENDPOINT:- `POST` **/authmanagement**

#### Request:-
```
{
  "action": "resetPwdLong", // default
  "value": 
	{ 
		"token": "5e31522aa52a1a023f3cda37___316bd7be299452aba5a1f4257849f7",   // this token will be found on the url
    	"password": "54321",    // the new password
	}
}
```
#### Response:-

* user object will be returned
```
{
    "_id": "5e31522aa52a1a023f3cda37",
    "activeConversationsIds": [],
    "cardsIds": [],
    "language": "en",
    "rolesIds": [
        "5e31522aa52a1a023f3cda38"
    ],
    "organizations": [
        "5e2eb10fc94f9d002f05a9a5"
    ],
    "accounts": [
        "5e2ecb776c8f6f01c905c16b"
    ],
    "accountModules": [],
    "email": "user3@beez.com",
    "isVerified": true,
    "createdAt": "2020-01-29T09:36:42.495Z",
    "updatedAt": "2020-01-29T09:36:42.548Z",
    "__v": 0,
    "beezInToAccount": "5e2ecb776c8f6f01c905c16b",
    "beezInToOrganization": "5e2eb10fc94f9d002f05a9a5"
}
```