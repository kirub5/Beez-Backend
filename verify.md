## Verifying Emails

* Is used to check if the user registered with a legit email
* All users should be verified after signup
* ENDPOINT:- `POST` **/authmanagement**

#### Request:-
```
{
	"action": "verifySignupShort",  // default
	"value": 
	{
		"user":
		{
			"email": "user2@beez.com"	// the user email
		},
    	"token": "196394" // 6 digit verification code which is sent to the user email
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
    "email": "user2@beez.com",
    "isVerified": true,
    "createdAt": "2020-01-29T09:36:42.495Z",
    "updatedAt": "2020-01-29T09:36:42.548Z",
    "__v": 0,
    "beezInToAccount": "5e2ecb776c8f6f01c905c16b",
    "beezInToOrganization": "5e2eb10fc94f9d002f05a9a5"
}
```