## Fetching owners

* Is used to fetch owners of organizations, accounts or modules
* Only **OWNERS** can fetch owners
* There are 3 levels:- 
    1. **ORGANIZATION** :- will return organization owners for the organization the user beezed in
    2. **ACCOUNT** :- will return account owners for the account the user beezed in
    3. **MODULE** :- will return module owners for the accountModule the user beezed in
* ENDPOINT:- `POST` **/fetch-users**

#### Request:-
- [x] Authorization required on header
```
{
	"level": "ACCOUNT"  // can be ORGANIZATION, ACCOUNT or MODULE, which will return owners of the specified level 
}
```
#### Response:-

* List of user objects will be returned
* Pending owners will be returned (Name and email)
```
{
    "total": 3,
    "limit": 30,
    "skip": 0,
    "data": [
        {
            "_id": "5e2eb9d80c6d4c004124880e",
            "activeConversationsIds": [],
            "cardsIds": [],
            "language": "en",
            "rolesIds": [
                "5e2ebc230c6d4c004124880f"
            ],
            "organizations": [
                "5e2eb10fc94f9d002f05a9a5"
            ],
            "accounts": [
                "5e2ecb776c8f6f01c905c16b",
                "5e2ed53d6c8f6f01c905c16d"
            ],
            "accountModules": [],
            "email": "user1@beez.com",
            "isVerified": false,
            "verifyExpires": "2020-02-01T10:22:16.396Z",
            "verifyToken": "78863aa07937047d0a596a9d010b28",
            "verifyShortToken": "305462",
            "createdAt": "2020-01-27T10:22:16.418Z",
            "updatedAt": "2020-01-27T12:20:21.322Z",
            "__v": 0,
            "beezInToOrganization": "5e2eb10fc94f9d002f05a9a5",
            "beezInToAccount": "5e2ecb776c8f6f01c905c16b",
            "beezInToModule": null,
            "currentOrganizationRole": {
                "_id": "5e2ebc230c6d4c004124880f",
                "organizationRole": "ORG_OWNER",
                "customOrganizationRoles": []
            },
            "currentAccountRole": {
                "accountRole": "ACCOUNT_OWNER",
                "customAccountRoles": [],
                "_id": "5e2ecb786c8f6f01c905c16c",
                "accountId": "5e2ecb776c8f6f01c905c16b"
            }
        },
        {
            "_id": "5e2fdab2ebc64a01051c1176",
            "activeConversationsIds": [],
            "cardsIds": [],
            "language": "en",
            "rolesIds": [
                "5e2fdab2ebc64a01051c1177"
            ],
            "organizations": [
                "5e2eb10fc94f9d002f05a9a5"
            ],
            "accounts": [],
            "accountModules": [],
            "email": "user3@beez.com",
            "isVerified": false,
            "verifyExpires": "2020-02-02T06:54:42.080Z",
            "verifyToken": "425b5d64c10593583de9685d18fe97",
            "verifyShortToken": "243697",
            "createdAt": "2020-01-28T06:54:42.084Z",
            "updatedAt": "2020-01-28T06:54:42.105Z",
            "__v": 0,
            "beezInToOrganization": "5e2eb10fc94f9d002f05a9a5",
            "currentOrganizationRole": {
                "_id": "5e2fdab2ebc64a01051c1177",
                "organizationRole": "ORG_OWNER",
                "customOrganizationRoles": []
            }
        },
        {
            "_id": "5e2fdc1fe822dd0113ddf42d",
            "activeConversationsIds": [],
            "cardsIds": [],
            "language": "en",
            "rolesIds": [
                "5e2fdc1fe822dd0113ddf42e"
            ],
            "organizations": [
                "5e2eb10fc94f9d002f05a9a5"
            ],
            "accounts": [
                "5e2ecb776c8f6f01c905c16b"
            ],
            "accountModules": [],
            "email": "user4@beez.com",
            "isVerified": false,
            "verifyExpires": "2020-02-02T07:00:47.206Z",
            "verifyToken": "fab2a9a6b18fb4e392c16676848256",
            "verifyShortToken": "110737",
            "createdAt": "2020-01-28T07:00:47.226Z",
            "updatedAt": "2020-01-28T07:00:47.302Z",
            "__v": 0,
            "beezInToAccount": "5e2ecb776c8f6f01c905c16b",
            "beezInToOrganization": "5e2eb10fc94f9d002f05a9a5",
            "currentOrganizationRole": {
                "_id": "5e2fdc1fe822dd0113ddf42e",
                "organizationRole": "ORG_MEMBER",
                "customOrganizationRoles": []
            },
            "currentAccountRole": {
                "accountRole": "ACCOUNT_OWNER",
                "customAccountRoles": [],
                "_id": "5e2fdc1fe822dd0113ddf42f",
                "accountId": "5e2ecb776c8f6f01c905c16b"
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
* Organization roles are :- **ORG_OWNER**, **ORG_MEMBER**
* Account roles are :- **ACCOUNT_OWNER**, **ACCOUNT_MEMBER**
* Module roles are :- **MODULE_OWNER**, **MODULE_MEMBER**, **SELECTOR**, **APPLICANT**
* ENDPOINT:- `POST` **/update-role**

#### Request:-
- [x] Authorization required on header
```
{
	"level": "Account", // Can be ORGANIZATION, ACCOUNT or MODULE
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