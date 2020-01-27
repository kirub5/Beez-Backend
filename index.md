# Backend API Documentation

This page is used to describe api's on our backend.

## Sign-up

* Is used to register a new user to beez buro.
* Endpoint:- **/users**

#### Request:-
```
{
    "email": "user1@beez.com", _email of the new user_
	"password": "12345", _password of the new user_
	"code": "COMP5050"        // _**(optional)** it is used if a user accepts invitation from an email_
}
```
#### Response:-

* The user object plus an access token is sent as a response

```
{
    "activeConversationsIds": [],
    "cardsIds": [],
    "language": "en",
    "rolesIds": [],
    "organizations": [],
    "accounts": [],
    "accountModules": [],
    "_id": "5e2e9f93c94f9d002f05a9a4",
    "email": "user1@beez.com",
    "isVerified": false,
    "createdAt": "2020-01-27T08:30:11.527Z",
    "updatedAt": "2020-01-27T08:30:11.527Z",
    "__v": 0,
    "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6ImFjY2VzcyJ9.eyJ1c2VySWQiOiI1ZTJlOWY5M2M5NGY5ZDAwMmYwNWE5YTQiLCJpYXQiOjE1ODAxMTM4MTEsImV4cCI6MTU4MDIwMDIxMSwiYXVkIjoiaHR0cHM6Ly95b3VyZG9tYWluLmNvbSIsImlzcyI6ImZlYXRoZXJzIiwic3ViIjoiNWUyZTlmODljOTRmOWQwMDJmMDVhOWEzIiwianRpIjoiMTYzMDBmMjYtMDRjNi00MjQyLWFmMmEtMzZmZjAwYmYyYmNhIn0.Y8fE1pIzflLD6BXR9SCtddX_a939gr9eveqv-c4jTHo"
}
```