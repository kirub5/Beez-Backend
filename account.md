## Creating Accounts

* Is used to create a new account
* Only **SYSTEM ADMINS** can create accounts
* ENDPOINT:- `POST` **/accounts**

#### Request:-
- [x] Authorization required on header
```
{
	"name": "Account One",  // Name of the new account
    "orgId": "5e4aa7e0f52617001dda4f45", // required
	"owners": ["user3@beez.com"],    // (optional) Owner for the account (this user will be invited by email)
	"domain": ["beez.com"], // (optional) Users only with the specified domains will join this account
}
```
#### Response:-

* The account object will be returned
* Organization will also be returned
```
{

    "_id": "5e4aa8f3f52617001dda4f46",
    "modulesIds": [],
    "accountOwnersIds": [],
    "domain": ["beez.com"],
    "pendingAccountOwners": ["user3@beez.com"],
    "name": "Account One",
    "orgId": "5e4aa7e0f52617001dda4f45",
    "createdAt": "2020-02-17T14:53:39.114Z",
    "updatedAt": "2020-02-17T14:53:39.510Z",
    "__v": 0,
    "organization": {
        "_id": "5e4aa7e0f52617001dda4f45",
        "accountsIds": [
            "5e4aa8f3f52617001dda4f46"
        ],
        "ownersUserIds": [],
        "pendingOrganizationOwners": [],
        "name": "Company One",
        "prefix": "COMP",
        "createdAt": "2020-02-17T14:49:04.580Z",
        "updatedAt": "2020-02-17T14:53:39.459Z",
        "__v": 0
    },
    "modules": [],
    "numberOfUsers": 0

}
```



## Fetching Accounts

* Is used to fetch accounts
* Only **SUPER ADMINS** or **ACCOUNT OWNERS** can fetch accounts
* ENDPOINT 1:- `GET` **/accounts** 
> _To fetch all accounts (for **SUPER ADMINS**)_
* ENDPOINT 2:- `GET` **/accounts/idOfAccount**    
> _To fetch a sepecific account_
* Users except **SUPER ADMINS** will get the account they are currently beezed in (So it is required for regular users to send accountid on the request header)

#### Request:-
- [x] Authorization required on header
- [x] accountid // required for non SUPERADMIN users
```
{
    // empty request body
}
```
#### Response:-

* List of accounts will be returned for ENDPOINT 1 (if the request is by a **SUPER ADMIN**)
* A specific account will be returned for ENDPOINT 2
* Only the account that the user is currently beezed in will be returned (if the request is by **ACCOUNT OWNER**)
* Organization will be attached

```
{
    "total": 1,
    "limit": 30,
    "skip": 0,
    "data": [
        {
            "_id": "5e2ecb776c8f6f01c905c16b",
            "modulesIds": [],
            "accountOwnersIds": [
                "5e2eb9d80c6d4c004124880e"
            ],
            "domain": ["beez.com"],
            "pendingAccountOwners": ["user3@beez.com"],
            "name": "Account One",
            "orgId": "5e2eb10fc94f9d002f05a9a5",
            "createdAt": "2020-01-27T11:37:27.756Z",
            "updatedAt": "2020-01-27T11:37:28.071Z",
            "__v": 0,
            "organization": {
            "_id": "5e4aa7e0f52617001dda4f45",
            "accountsIds": [
                "5e4aa8f3f52617001dda4f46"
            ],
            "ownersUserIds": [],
            "pendingOrganizationOwners": [],
            "name": "Company One",
            "prefix": "COMP",
            "createdAt": "2020-02-17T14:49:04.580Z",
            "updatedAt": "2020-02-17T14:53:39.459Z",
            "__v": 0
        },
            "modules": [],
            "numberOfUsers": 1
        }
    ]
}
```



## Updating Accounts

* Is used to patch an account
* Only **SUPER ADMINS** or **ACCOUNT OWNERS** can update an account
* **ACCOUNT OWNERS** can only update organizations that they are currently beezed in (So they need to send accountid on the request header)
* ENDPOINT:- `PATCH` **/accounts/idOfAccount**

#### Request:-
- [x] Authorization required on header
- [x] accountid required for non SUPERADMIN users

```
{
	"name": "Account_One",
    "description": "Some description"
}
```
#### Response:-

* The updated account will be returned
* Organization is attached to the response
```
{
    "_id": "5e2ecb776c8f6f01c905c16b",
    "modulesIds": [],
    "accountOwnersIds": [
        "5e2eb9d80c6d4c004124880e"
    ],
    "domain": ["beez.com"],
    "pendingAccountOwners": ["user3@beez.com"],
    "name": "Account_One",
    "description": "Some description",
    "orgId": "5e2eb10fc94f9d002f05a9a5",
    "createdAt": "2020-01-27T11:37:27.756Z",
    "updatedAt": "2020-01-27T11:52:51.181Z",
    "__v": 0,
    "organization": {
        "_id": "5e4aa7e0f52617001dda4f45",
        "accountsIds": [
            "5e4aa8f3f52617001dda4f46"
        ],
        "ownersUserIds": [],
        "pendingOrganizationOwners": [],
        "name": "Company One",
        "prefix": "COMP",
        "createdAt": "2020-02-17T14:49:04.580Z",
        "updatedAt": "2020-02-17T14:53:39.459Z",
        "__v": 0
    },
}
```