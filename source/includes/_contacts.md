# Contacts

Contacts in Checkbox 7 take the place of "Users" in Checkbox 6. Contacts are both administrative users and survey respondents.

You can utilize this endpoint to retrieve contact data, edit contacts, and delete contacts.

## Get Contacts

> To get a list of contacts: 

```shell
curl -X GET -H "Content-type: application/json" -H "Authorization: Bearer {ACCESS_TOKEN}" ^
"{ACCOUNT_NAME}/contacts?search_text=admin&sort_ascending=True&page_size=2&page_num=3"
```

> The above command returns JSON structured like this: 

```json
{  
   "total_count":15,
   "items":[  
      {  
         "unique_identifier":"Test",
         "user_name":"Test",
         "email":"jon.doe@gmail.com",
         "status":"Active"
      }
   ],
   "paging_info":{  
      "page_size":0,
      "page_num":1
   },
   "has_next":false,
   "has_previous":false
}
```

This endpoint will return a paged, filtered list of contacts.

### HTTP Request

`GET {ACCOUNT_NAME}/contacts`

### Query Parameters

Parameter | Required | Data Type | Description
--------- | ------- | ------- | -----------
search_text | False |  string | Used for searching by name
sort_ascending | False | bool | Sort returned by username ascending
page_size | False  | int | Size of pages to be returned
page_num | False | int | Number of page to be returned

## Get Contact

> To get a list of contacts: 

```shell
curl -X GET -H "Content-type: application/json" -H "Authorization: Bearer {ACCESS_TOKEN}" ^
"{ACCOUNT_NAME}/contacts/Test"
```

> The above command returns JSON structured like this: 

```json
{  
   "unique_identifier":"Test",
   "user_name":"Test",
   "email":"jon.doe@gmail.com",
   "status":"Active"
}
```

This endpoint will return the contact data for a single contact specified by its unique identifier .

`GET {ACCOUNT_NAME}/contacts/{UNIQUE_IDENTIFIER}`

## Create Contact

> To create the contact: 

```shell
curl -X POST -H "Content-type: application/json" -H "Authorization: Bearer {ACCESS_TOKEN}" ^
 -d '{ "user_name": "newuser", "email": "newuser@email.com", "password":"pa$$w0rd" }' ^
 "{ACCOUNT_NAME}/contacts"
```

> The above command returns JSON structured like this:

```json
{  
   "unique_identifier":"Test1",
   "user_name":"Test1",
   "email":"jon.doe@gmail.com",
   "status":"Active"
}
```

This endpoint will create a contact with the username, email, and password specified. 

### HTTP Request

`POST {ACCOUNT_NAME}/contacts`

### Request Body Arguments

Parameter | Required | Data Type | Description
--------- | ------- | ------- | -----------
user_name | True  | string | Contact name
password | True  | string | Contact Password
email | True  | string | Contact Email


## Edit Contact

> To edit the contact: 

```shell
curl -X POST -H "Content-type: application/json" -H "Authorization: Bearer {ACCESS_TOKEN}" ^
 -d '{ "user_name": "test22", "email": "newuser2@email.com", "password":"pa$$w0rd", "status": "Active" }' ^
 "{ACCOUNT_NAME}/contacts/test1"
```

> The above command returns JSON structured like this

```json
{  
   "unique_identifier":"Test1",
   "user_name":"Test1",
   "email":"jon.doe@gmail.com",
   "status":"Active"
}
```

This endpoint can be utilized to edit a contacts username, email or password, or enable / disable the contacts account. Contact profile property data can be edited using the edit contact profile data endpoint documented below.

### HTTP Request

`PUT {ACCOUNT_NAME}/contacts/{UNIQUE_IDENTIFIER}`

### Request Body Arguments

Parameter | Required | Data Type | Description
--------- | ------- | ------- | -----------
user_name | False | string | Contact name
password | False | string | Contact Password
email | False | string | Contact Email
status | False | enum | For status specifying (default=active): Active or LockedOut 


## Delete Contact

> To delete the contact

```shell
curl -X DELETE -H "Content-type: application/json" -H "Authorization: Bearer {ACCESS_TOKEN}" ^
 "{ACCOUNT_NAME}/contacts/test1"
```

> The above command returns an HTTP status code of 200 OK when successful

This endpoint can be utilized to delete a contact. This will not prompt for a confirmation and this action cannot be undone. 

### HTTP Request

` DELETE {ACCOUNT_NAME}/contacts/{UNIQUE_IDENTIFIER} `

<aside class="warning">Deleting a contact is permanent. Once a contact is deleted they cannot be restored.</aside>


## Get Contact Group Memberships
## Add Contact to Group 
## Remove Contact from Group
## Get Contacts Roles
## Add Roles to Contact
## Remove Contact Roles
## Get Contact Profile Data
## Edit Contact Profile Data

