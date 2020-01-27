## Switching

* Is used when a user switchs between multiple orgainzations, accounts or modules.
* Will help us know to which specific organization, account or module a user is currently beezed in to
* ENDPOINT:- `POST` **/switch**

#### Request:-
- [x] Authorization required on header
- Options are toOrganization, toAccount and toModule.
- One of these 3 will be used to switch from the same level, but combination of the 3 could be used to switch on different levels. For example to switch to an account in the same organization we will only use `toAccount`, But to switch to an account in a different organization we will use `toOrganization` and `toAccount`.

```
{   
    "toOrganization": "5e2ecb776c8f6f01c905c16b",   // To with organization to switch
    "toAccount": "5e2ecb776c8f6f01c905c16b",    // To which account to switch 
    "toModule" : "5e2ecb776c8f6f01c905c16b" // To which module to switch
}
```
#### Response:-

* The user object will be returned
```
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
    "email": "user3@beez.com",
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
}
```