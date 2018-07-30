# Authentication

> To retrieve authentication token

```shell
curl "{ACCOUNT_NAME}/oauth2/token" 
        -d "grant_type=password&username={USERNAME}&password={PASSWORD}"
```


> The above command returns JSON structured like this:

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

