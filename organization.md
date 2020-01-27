## Creating Organizations

* Is used to create a new organization.
* Only **SUPER ADMINS** can create organizations
* ENDPOINT:- `POST` **/organizations**

#### Request:-
[x] Authorization required on header
```
{
	"name": "Company One",  // Name of the new organization
	"owner": "user2@beez.com",    // Owner of the organization (this user will be invited by email)
	"prefix": "COMP", // 4 letter unique identifier for the organization (if left blank, the first 4 letters of the organization name will be assigned)
}
```
#### Response:-

* The organization object will be returned
```
{
    "accountsIds": [],
    "ownersUserIds": [],
    "pendingOrganizationOwners": [],
    "_id": "5e2eb10fc94f9d002f05a9a5",
    "name": "Company One",
    "prefix": "COMP",
    "createdAt": "2020-01-27T09:44:47.994Z",
    "updatedAt": "2020-01-27T09:44:47.994Z",
    "__v": 0
}
```



## Fetching Organizations

* Is used to fetch organizations
* Only **SUPER ADMINS** or **ORGANIZATION OWNERS** can fetch organizations
* ENDPOINT 1:- `GET` **/organizations** 
> _To fetch all organizations (for **SUPER ADMINS**)_
* ENDPOINT 2:- `GET` **/organizations/idOfOrganization**    
> _To fetch a sepecific organization_

#### Request:-
[x] Authorization required on header
```
{

}
```
#### Response:-

* List of organizations will be returned for ENDPOINT 1 (if the request is by a **SUPER ADMIN**)
* A specific organization will be returned for ENDPOINT 2
* Only the organization that the user is currently beezed in will be returned (if the request is by an **ORGANIZATION OWNER**)

```
{
    "total": 1,
    "limit": 30,
    "skip": 0,
    "data": [
        {
            "_id": "5e2eb10fc94f9d002f05a9a5",
            "accountsIds": [],
            "ownersUserIds": [],
            "pendingOrganizationOwners": [
                "user2@beez.com"
            ],
            "name": "Company ONE",
            "prefix": "COMP",
            "createdAt": "2020-01-27T09:44:47.994Z",
            "updatedAt": "2020-01-27T09:44:48.610Z",
            "__v": 0,
            "accounts": []
        }
    ]
}
```



## Updating Organizations

* Is used to patch an organization
* Only **SUPER ADMINS** or **ORGANIZATION OWNERS** can update an organization
* **ORGANIZATION OWNERS** can only update organizations that they are currently beezed in
* ENDPOINT:- `PATCH` **/organizations/idOfOrganization**

#### Request:-
[x] Authorization required on header
```
{
	"name": "Company One",
}
```
#### Response:-

* The updated organization will be returned
```
{
    "_id": "5e2eb10fc94f9d002f05a9a5",
    "accountsIds": [],
    "ownersUserIds": [
        "5e2eb9d80c6d4c004124880e"
    ],
    "pendingOrganizationOwners": [],
    "name": "Company One",
    "prefix": "COMP",
    "createdAt": "2020-01-27T09:44:47.994Z",
    "updatedAt": "2020-01-27T11:10:30.959Z",
    "__v": 0
}
```