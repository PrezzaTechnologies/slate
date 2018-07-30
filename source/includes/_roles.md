# Roles

## Get System Roles


> To retrieve the survey / folder list: 

```shell
curl -X GET -H "Content-type: application/json" -H "Authorization: Bearer {ACCESS_TOKEN}"  ^
"{ACCOUNT_NAME}/roles"
```

> The above command returns JSON structured like this:

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

This endpoint returns all roles available to users. These roles can then be utilized in the create / update contact methods to assign roles to contacts.

### HTTP Request

`GET {ACCOUNT_NAME}/roles`


