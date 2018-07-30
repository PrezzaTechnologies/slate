# Survey List

## Get Survey List

> To retrieve the survey / folder list: 

```shell
curl -X GET -H "Content-type: application/json" -H "Authorization: Bearer <ACCESS_TOKEN>"  ^
"{ACCOUNT_NAME}/survey-list?search_text=&folder_id=&is_favorite=false&page_size=3&page_num=0&status=Archived"
```

> The above command returns JSON structured like this:

```json
{  
   "total_count":2,
   "items":[  
      {  
         "id":1311,
         "list_item_type":"SurveyFolder",
         "name":"Folder1",
         "activation_start_date":null,
         "is_favorite":false,
         "status":null,
         "response_limit":null,
         "response_count":null,
         "can_edit":true,
         "can_administer":true,
         "can_create_report":true,
         "can_view_responses":true
      },
      {  
         "id":1312,
         "list_item_type":"SurveyFolder",
         "name":"Folder2",
         "activation_start_date":null,
         "is_favorite":false,
         "status":null,
         "response_limit":null,
         "response_count":null,
         "can_edit":true,
         "can_administer":true,
         "can_create_report":true,
         "can_view_responses":true
      }
   ],
   "paging_info":{  
      "page_size":3,
      "page_num":0
   },
   "has_next":false,
   "has_previous":false
}
```

This endpoint returns all surveys the authenticated user has access to. This method is searchable using the "search_text" parameter and paged using "page_size" and "page_num" parameters. 

### HTTP Request

`GET {ACCOUNT_NAME}/survey-list`

### Query Parameters

Parameter | Required | Data Type | Description
--------- | ------- | ------- | -----------
search_text | False |  string | Used for searching by name
folder_id | False | int | Used to list only surveys in specific folder
is_favorite | False  | bool | Used to filter on only favorites (default is false)
page_size | False  | int | Size of pages to be returned
page_num | False | int | Number of page to be returned
status | False | string | Used to filter by survey status


