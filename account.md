## Creating Accounts

* Is used to create a new account
* Only **ORGANIZATION OWNERS** can create accounts
* ENDPOINT:- `POST` **/accounts**

#### Request:-
- [x] Authorization required on header
```
{
	"name": "Account One",  // Name of the new account
	"owner": "user3@beez.com",    // (optional) Owner for the account (this user will be invited by email)
	"domain": ["beez.com"], // (optional) Users only with the specified domains will join this account
}
```
#### Response:-

* The account object will be returned
```
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
    "modules": [],
    "numberOfUsers": 1
}
```



## Fetching Accounts

* Is used to fetch accounts
* Only **SUPER ADMINS**, **ORGANIZATION OWNERS** or **ACCOUNT OWNERS** can fetch accounts
* ENDPOINT 1:- `GET` **/accounts** 
> _To fetch all accounts (for **SUPER ADMINS**)_
* ENDPOINT 2:- `GET` **/accounts/idOfAccount**    
> _To fetch a sepecific account_
* Users except **SUPER ADMINS** will get the account they are currently beezed in

#### Request:-
- [x] Authorization required on header
```
{
    // empty request body
}
```
#### Response:-

* List of accounts will be returned for ENDPOINT 1 (if the request is by a **SUPER ADMIN**)
* A specific account will be returned for ENDPOINT 2
* Only the account that the user is currently beezed in will be returned (if the request is by an **ORGANIZATION OWNER** or **ACCOUNT OWNER**)

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
            "modules": [],
            "numberOfUsers": 1
        }
    ]
}
```



## Updating Accounts

* Is used to patch an account
* Only **SUPER ADMINS**, **ORGANIZATION OWNERS** or **ACCOUNT OWNERS** can update an account
* **ORGANIZATION OWNERS** and **ACCOUNT OWNERS** can only update organizations that they are currently beezed in
* ENDPOINT:- `PATCH` **/accounts/idOfAccount**

#### Request:-
- [x] Authorization required on header
```
{
	"name": "Account_One",
    "description": "Some description"
}
```
#### Response:-

* The updated account will be returned
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
    "__v": 0
}
```