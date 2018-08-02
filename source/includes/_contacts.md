# Contacts

Contacts in Checkbox 7 take the place of "Users" in Checkbox 6. Contacts are both administrative users and survey respondents.

You can utilize this endpoint to retrieve contact data, edit contacts, and delete contacts.

## Get Contacts

> Example Request

```shell
curl --request GET \
  --url '{ACCOUNT_NAME}/contacts?search_text=test&sort_ascending=true&page_size=3&page_num=1'
```

```python
import requests

url = "{ACCOUNT_NAME}/contacts"

querystring = {"search_text":"test","sort_ascending":"true","page_size":"3","page_num":"1"}

response = requests.request("GET", url, params=querystring)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("{ACCOUNT_NAME}/contacts?search_text=test&sort_ascending=true&page_size=3&page_num=1")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body
```
> Example Response

```json
{  
   "total_count":15,
   "items":[  
      {  
         "id":"Test",
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

This endpoint will return a paged, filtered list of contacts that the authenticated user has access to. System administrators by default have access to all contacts, any lower role will only have access to contacts that are part of groups that they have access to. 

To grant a user access to all contacts you can grant them access to the "Contact List" which is the complete list of contacts in the Checkbox account.


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

> Example Request

```shell
curl --request GET \
  --url '{ACCOUNT_NAME}/contacts/test'
```

```python
import requests

url = "{ACCOUNT_NAME}/contacts/test"

response = requests.request("GET", url)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("{ACCOUNT_NAME}/contacts/test")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body
```

> Example Response

```json
{  
   "id":"Test",
   "email":"jon.doe@gmail.com",
   "status":"Active"
}
```

This endpoint will return the contact data for a single contact specified by its contact ID. This endpoint will only return data for the contact if the authenticated user has access to the contact being requested.

`GET {ACCOUNT_NAME}/contacts/{CONTACT_ID}`


## Create Contact

> Example Request

```shell
curl --request POST \
  --url {ACCOUNT_NAME}/contacts \
  --header 'Content-Type: application/json' \
  --data ' { "id": "newuser", "email": "newuser@email.com", "password":"pa$$w0rd" }'
```

```python
import requests

url = "{ACCOUNT_NAME}/contacts"

payload = " { \"id\": \"newuser\", \"email\": \"newuser@email.com\", \"password\":\"pa$$w0rd\" }"
headers = {'Content-Type': 'application/json'}

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("{ACCOUNT_NAME}/contacts")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Post.new(url)
request["Content-Type"] = 'application/json'
request.body = " { \"id\": \"newuser\", \"email\": \"newuser@email.com\", \"password\":\"pa$$w0rd\" }"

response = http.request(request)
puts response.read_body
```
> Example Response

```json
{
    "id": "newuser",
    "email": "newuser@testemail.com",
    "status": "Active"
}
```

This endpoint will create a contact with the id, email, and password specified. It will also add the contact to the specified group IDs. 

The password field is optional. If no password is provided the system will auto generate one. 

Group ID list is optional for users with access to the "Contact List". Any user without access to the "Contact List" must provide a group ID for a group they have access to or the contact will not be created. 

### HTTP Request

`POST {ACCOUNT_NAME}/contacts`

### Request Body Arguments

Parameter | Required | Data Type | Description
--------- | ------- | ------- | -----------
id | True  | string | Contact id
password | True  | string | Contact Password
email | True  | string | Contact Email

## Edit Contact

> Example Request

```shell
curl --request PUT \
  --url {ACCOUNT_NAME}/contacts/newuser \
  --header 'Content-Type: application/json' \
  --data '{ "id": "test22", "email": "newuser2@email.com", "password":"pa$$w0rd", "status": "Active" }'
```

```python
import requests

url = "{ACCOUNT_NAME}/contacts/newuser"

payload = "{ \"id\": \"test22\", \"email\": \"newuser2@email.com\", \"password\":\"pa$$w0rd\", \"status\": \"Active\" }"
headers = {'Content-Type': 'application/json'}

response = requests.request("PUT", url, data=payload, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("{ACCOUNT_NAME}/contacts/newuser")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Put.new(url)
request["Content-Type"] = 'application/json'
request.body = "{ \"id\": \"test22\", \"email\": \"newuser2@email.com\", \"password\":\"pa$$w0rd\", \"status\": \"Active\" }"

response = http.request(request)
puts response.read_body
```

> Example Response

```json
{  
   "unique_identifier":"Test22",
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
id | False | string | Contact name
password | False | string | Contact Password
email | False | string | Contact Email
status | False | enum | For status specifying (default=active): Active or LockedOut 


## Delete Contact
## Get Contact Group Memberships
## Add Contact to Group 
## Remove Contact from Group
## Get Contacts Roles
## Add Roles to Contact
## Remove Contact Roles
## Get Contact Profile Data
## Edit Contact Profile Data

