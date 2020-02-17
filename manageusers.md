## Fetching owners

* Is used to fetch owners of organizations, accounts or modules
* Only **OWNERS** can fetch owners
* There are 2 levels:- 
    1. **ACCOUNT** :- will return account owners for the account the user beezed in
    2. **MODULE** :- will return module owners for the accountModule the user beezed in
* ENDPOINT:- `POST` **/fetch-users**
* If the level is set to **ACCOUNT**, accountid should be attached to the request header
* * If the level is set to **MODULE**, accountid and accountmoduleid should be attached to the request header

#### Request:-
- [x] Authorization required on header
- [x] accountid required
- [x] accountmoduleid required if the level is **MODULE**
```
{
	"level": "ACCOUNT"  // can be ACCOUNT or MODULE, which will return users of the specified level 
}
```
#### Response:-

* List of user objects will be returned
* Pending owners will be returned (Name and email)
* Current Account Role or Current Module Role are fields that show what role the user has in the fetched account or module


```
{
    "total": 1,
    "limit": 30,
    "skip": 0,
    "data": [
        {
            "_id": "5e4aac70f52617001dda4f48",
            "activeConversationsIds": [],
            "cardsIds": [],
            "language": "en",
            "rolesIds": [
                "5e4aac95f52617001dda4f49"
            ],
            "accounts": [
                "5e4aa8f3f52617001dda4f46"
            ],
            "accountModules": [],
            "email": "user1@beez.com",
            "isVerified": false,
            "verifyExpires": "2020-02-22T15:08:32.284Z",
            "verifyToken": "e6bc905cb2a33d8982a991c7382aae",
            "verifyShortToken": "211926",
            "createdAt": "2020-02-17T15:08:32.286Z",
            "updatedAt": "2020-02-17T15:09:09.713Z",
            "__v": 0,
            "currentAccountRole": {
                "_id": "5e4aac95f52617001dda4f49",
                "accountRole": "ACCOUNT_OWNER",
                "customAccountRoles": [],
                "accountPermissions": [],
                "userId": "5e4aac70f52617001dda4f48",
                "accountId": "5e4aa8f3f52617001dda4f46",
                "moduleRoles": [],
                "createdAt": "2020-02-17T15:09:09.709Z",
                "updatedAt": "2020-02-17T15:09:09.709Z",
                "__v": 0
            }
        }
    ],
    "pending": [
        {
            "_id": "5e314062777c6a001d4c1b77",
            "name": "user 6",
            "email": "user6@beez.com"
        }
    ]
}
```



## Changing roles

* Is used to change role of a user
* Only **OWNERS** can change other user's roles
* Account roles are :- **ACCOUNT_OWNER**, **ACCOUNT_MEMBER**
* Module roles are :- **MODULE_MEMBER**, **SELECTOR**, **APPLICANT**
* ENDPOINT:- `POST` **/update-role**

#### Request:-
- [x] Authorization required on header
- [x] accountid should be on the header
- [x] accountmoduleid should be on the header if the level is 'Module'


```
{
	"level": "Account", // Can be ACCOUNT or MODULE
	"userId": "5e2fdc1fe822dd0113ddf42d",   // id of the victom user
	"newRole": "ACCOUNT_MEMBER" // The new Role
}
```
#### Response:-

* user object will be returned (with id, rolesIds and email)
```
{
    "_id": "5e2fdc1fe822dd0113ddf42d",
    "rolesIds": [
        "5e2fdc1fe822dd0113ddf42e"
    ],
    "email": "user5@beez.com"
}
```