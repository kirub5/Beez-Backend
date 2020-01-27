## Login

* Is used to login a user to beez buro.
* Endpoint:- `POST` **/authentication**

#### Request:-

```
{
	"strategy": "local",    // for now only use local
	"email": "user3@beez.com",   // email of the user
	"password": "12345",    // password of the user
    "code": "COMP5050"        // (optional) it is used if a user accepts invitation from an email
}
```
#### Response:-

* The user object plus an access token is returned as a response

```
{
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
    "accounts": [],
    "accountModules": [],
    "email": "user3@beez.com",
    "isVerified": false,
    "verifyExpires": "2020-02-01T10:22:16.396Z",
    "verifyToken": "78863aa07937047d0a596a9d010b28",
    "verifyShortToken": "305462",
    "createdAt": "2020-01-27T10:22:16.418Z",
    "updatedAt": "2020-01-27T10:32:03.122Z",
    "__v": 0,
    "beezInToOrganization": "5e2eb10fc94f9d002f05a9a5",
    "currentOrganizationRole": {
        "_id": "5e2ebc230c6d4c004124880f",
        "organizationRole": "ORG_OWNER",
        "customOrganizationRoles": []
    },
    "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6ImFjY2VzcyJ9.eyJpYXQiOjE1ODAxMjEyNDcsImV4cCI6MTU4MDIwNzY0NywiYXVkIjoiaHR0cHM6Ly95b3VyZG9tYWluLmNvbSIsImlzcyI6ImZlYXRoZXJzIiwic3ViIjoiNWUyZWI5ZDgwYzZkNGMwMDQxMjQ4ODBlIiwianRpIjoiOWIyYmU5ZjQtNTJjMS00ODM5LTgxOTItYTViNmQzMzEyYzM0In0.DvLMQh4vNimF2uSPR5ZRUuFfZFztbNKFw9hMs4mu0Yw"
}
}
```