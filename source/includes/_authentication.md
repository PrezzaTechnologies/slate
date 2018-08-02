# Authentication

## Authenticate

> Example Request

```shell
curl --request POST \
  --url {ACCOUNT_NAME}/oauth2/token \
  --header 'Content-Type: application/x-www-form-urlencoded' \
  --data 'username=test&password=test&grant_type=password'
```

```ruby
require 'uri'
require 'net/http'

url = URI("{ACCOUNT_NAME}/oauth2/token")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Post.new(url)
request["Content-Type"] = 'application/x-www-form-urlencoded'
request.body = "username=test&password=test&grant_type=password"

response = http.request(request)
puts response.read_body
```

```python
import requests

url = "{ACCOUNT_NAME}/oauth2/token"

payload = "username=test&password=test&grant_type=password"
headers = {'Content-Type': 'application/x-www-form-urlencoded'}

response = requests.request("POST", url, data=payload, headers=headers)
```


> Example Response

```json
{  
   "access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9",
   "token_type":"bearer",
   "expires_in":43199,
   "user_name":"admin",
   "roles":"System Administrator",
   "account_name":"apiaccount",
   "hosts":"developer.checkboxonline.com"
}
```
In order to utilize the API you will need to first retrieve an OAuth token from the API. This can be done using the  {ACCOUNT_NAME}/oauth2/token  endpoint passing in your username and password. An example request can be found on the right hand side. 

Once the request has been verified you will receive an authentication token that you will pass in the authentication header in subsequent requests. This token will expire if not used and you may need to request a new one. 

`-H "Authorization: Bearer {AUTH-TOKEN}"`


### Headers

Content-Type | application/x-www-form-urlencoded

### Request Body Arguments (url encoded)

Parameter | Required | Data Type | Description
--------- | ------- | ------- | -----------
username  | True  | string | Contact id / name
password | True  | string | Contact Password
grant_type | True | enum | Accepted values: "password" 

