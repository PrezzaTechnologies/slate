# Roles

Roles in Checkbox control what a contact / user has access to do, not what they can access. Assign roles to give users the ability to complete certain actions in Checkbox. To grant them access to content in Checkbox you will need to grant them specific access to that content using the access lists. 

Access list methods can be found under each individual resources method list.

## Get System Roles


> Example Request

```shell
curl --request GET \
  --url '{ACCOUNT_NAME}/roles'
```

```python
import requests

url = "{ACCOUNT_NAME}/roles"

response = requests.request("GET", url)

print(response.text)
```

```ruby 
require 'uri'
require 'net/http'

url = URI("{ACCOUNT_NAME}/roles")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body
```

> Example Response

```json
[  
   "System Administrator",
   "User Administrator",
   "Survey Administrator",
   "Respondent",
   "Report Viewer",
   "Report Administrator",
   "Survey Editor",
   "Group Administrator"
]
```

This endpoint returns all the roles available to users. These roles can then be added to a contact / user to grant them ability to complete different actions in Checkbox. More detailed information on what each role can do can be found in our end user documentation.

### HTTP Request

`GET {ACCOUNT_NAME}/roles`


