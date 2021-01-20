**setExtraCurricularDataUploadUtility**
----
	Returns "success" and a count of updated students, or a structure of invalid validations "__invalid" belonging to student(s).

* **Version:**

	2

* **Method:**

	`GET | POST`
	
*  **Params:**

	**Required:**
 
	`ecactivity [array]` - Array of Students to be updated

	`id [string]` - Student Code
  
	`act_code [string]` - Activity Code
  
	`act_year [string]` - Activity Year
  
	`act_sem [string]` - Activity Semester

	**Optional:** (one or more optional fields required)
  
	`unit_num [smallint]` - unit number
  
	`act_level [string]` - Activity Level
	
	`ecaud1_code [string]` to `ecaud10_text [string]` - User Defined Codes
	
	`com_text [string]` - Comment
	
	`priority_flg [string]` - Priority flag
	
	`stud_ack_flg [string]` - Student acknowledgement flag
	
	`par_ack_flg [string]` - Parent acknowledgement flag
	
	`ecaud1_flg [string]` to `ecaud10_flg [string]` - User Defined Flags
	
	`ecaud11_code [string]` to `ecaud20_code [string]` - User Defined Codes
	
	`ecaud21_text [string]` to `ecaud25_text [string]` - User Defined Text

* **Success Response:**

	```javascript
	{
		"success": "You successfully saved 1 student(s).",
		"__tassversion": "01.000.043.0",
		"token": {
			"act_year": 2018,
			"act_code": "001",
			"timestamp": "{ts '2021-01-20 11:34:52'}",
			"act_sem": 1,
			"id": "0009130",
			"ecactivity": [
					{
						"ecud1_code": 4,
						"act_level": "",
						"act_year": 2018,
						"stud_code": "0009130",
						"act_code": "001",
						"companyCode": 10,
						"id": "0009130",
						"ecud2_code": 2,
						"act_sem": 1,
						"unit_num": ""
					}
			]
		}
	}
	```
 
* **Error Response:**

	`ecactivity` not supplied
	```javascript
	__invalid: {
		"ecactivity": "'ecactivity' is required."
	}
	```

	`[field_name]` is not valid
	```javascript
	__invalid: {
		"[field_name]": "'[field_name]' is not a valid field name"
	}
	```

	`id` not supplied
	```javascript
	__invalid: {
		"id": "Id is required for all rows."
	}
	```

	`id` has a duplicate value
	```javascript
	__invalid: {
		"id": "Id must be unique for all rows."
	}
	```

	`id` not a valid student code
	```javascript
	__invalid: {
		"stud_code": "Invalid Student Code."
	}
	```

	`act_code` length less than 1
	```javascript
	__invalid: {
		"act_code": "field is required."
	}
	```

	`act_year` length less than 1
	```javascript
	__invalid: {
		"given_name": "field is required."
	}
	```

	`act_sem` length less than 1
	```javascript
	__invalid: {
		"preferred_name": "field is required."
	}
	```

	`act_code` is not a valid code in ecactivity table
	```javascript
	__invalid: {
		"act_code": "<activity from file> is not a valid activity."
	} 
	```

	`act_year` is not a numeric value from 1900 to 2100
	```javascript
	__invalid: {
		"act_year": "Must be a numeric value from 1900 to 2100. Year: <year from file>."
	} 
	```

	`act_sem` is not a positive number less than or equal to srparms.semester_max
	```javascript
	__invalid: {
		"act_sem": "Must be a numeric value from 1 to < srparms.semester_max >”.  Semester/Term: <semester/term from file>."
	} 
	```

	`unit_num` is passed in and ecparms.unit_text is NULL
	```javascript
	__invalid: {
		"unit_num": "The Extra Curricular module is not setup to record Unit."
	} 
	```

	`unit_num` is not a positive number less than or equal to ecparms.unit_max
	```javascript
	__invalid: {
		"unit_num": "Must be a numeric value from 1 to < ecparms.unit_max >”.  Unit: <unit from file>."
	} 
	```

	`act_level` is not a valid lev_code in the ecalevel table
	```javascript
	__invalid: {
		"act_level": "<level from file> is not a valid Level."
	} 
	```

	`priority_flg` exceed 1 characters
	```javascript
	__invalid: {
		"priority_flg": "exceeds 1 characters."
	} 
	```

	`stud_ack_flg` exceed 1 characters
	```javascript
	__invalid: {
		"stud_ack_flg": "exceeds 1 characters."
	} 
	```

	`par_ack_flg` exceed 1 characters
	```javascript
	__invalid: {
		"par_ack_flg": "exceeds 1 characters."
	} 
	```

	`ecud1_code [string]` to `ecud5_code [string]` exceed 3 character
	```javascript
	__invalid: {
		"[field]": "[field] exceeds [field's length limit] characters."
	} 
	```

	`ecud6_text [string]` to `ecud10_text [string]` exceed 20 characters
	```javascript
	__invalid: {
		"[field]": "[field] exceeds [field's length limit] characters."
	} 
	```

	`ecaud1_flg [string]` to `ecaud10_flg [string]` exceed 1 characters
	```javascript
	__invalid: {
		"[field]": "[field] exceeds [field's length limit] characters."
	} 
	```
	
	`ecaud1_flg [string]` to `ecaud10_flg [string]` is not alphanumeric
	```javascript
	__invalid: {
		"[field]": "Value is not a valid alphanumeric code."
	} 
	```

	`ecaud11_code [string]` to `ecaud20_code [string]` exceed 3 characters
	```javascript
	__invalid: {
		"[field]": "[field] exceeds [field's length limit] characters."
	} 
	```

	`ecaud21_text [string]` to `ecaud25_text [string]` exceed 20 characters
	```javascript
	__invalid: {
		"[field]": "[field] exceeds [field's length limit] characters."
	} 
	```

* **Sample Parameters:**

	```javascript
	{
		"act_code":"001",
		"act_year":"2018",
		"act_sem":"1",
		"id":"0009130",
		"ecactivity":
		[
			{
				"id":"0009130",
				"ecud1_code":"4",
				"ecud2_code":"2",
				...
			}
		]
	 }
	```

* **Sample GET:** (With URL Encoded `token`)

	```HTML
	http://api.tasscloud.com.au/tassweb/api/?method=setExtraCurricularDataUploadUtility&appcode=UPLOAD&company=10&v=2&token=BJVvYXC0We4Dtvp6Q49RqhBeAi6uqpTQ9t%2FKI9ZAFpCMeVXIFlDU5yNQIeYME%2BYLXgYA69RTUjXjLeVBetN6CaFMdPCKMWBXD%2Bkkt0%2Fuht0suYrSDONP6mx%2Fbt4WGgNOD5YoIYRNiIVDw2Qn2Oi5YodaEUgtGJohUJMzy3tqsX%2BraZk3j7d77okDCjb7MeFJ0DcupqUoRiGjE39415HTfPgNc6R6BY9wt7SJsj4yOPBrIxHQVS8Yy6gZ3nZgsJ5rhcdkB6eCI6b3FJ31s6vsVcbVu5NBY8AF1qqjWLMazduISzEBwRDsofXfJjo1KLX59R410bmbrF5Z7QZfEfE%2FlettTWOyb4EgdhBoC3v0aLOfF6Bt12AFXDo2VGbgryceeOLAscp%2FFr9ttH42hClBtWsxFU1N5dDENUsVHOwWcfCxd7aTtc0xjvaEYJWcZrRRZa1yrIvgeWaDk0LVxM5ePcT%2BltdrymgmxmZYgxdiYC1qQDcNXDx9hN7yKeZDUztwGA0yl2iXW8aBXAy5hRnztR0TrREyOba26mUHxUJO7tfpIyOrpPbE0nR18vtCZ%2BinbvyqN9adpZhQPByG2XD9M6MoYdmBCc3Duv9qb%2BIa0A8%3D
	```
	
* **Sample POST:**

	```HTML
	<form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
		 <input type="hidden" name="method" value="setExtraCurricularDataUploadUtility">
		 <input type="hidden" name="appcode" value="UPLOAD">
		 <input type="hidden" name="company" value="10">
		 <input type="hidden" name="v" value="2">
		 <textarea name="token">BJVvYXC0We4Dtvp6Q49RqhBeAi6uqpTQ9t/KI9ZAFpCMeVXIFlDU5yNQIeYME+YLXgYA69RTUjXjLeVBetN6CaFMdPCKMWBXD+kkt0/uht0suYrSDONP6mx/bt4WGgNOD5YoIYRNiIVDw2Qn2Oi5YodaEUgtGJohUJMzy3tqsX+raZk3j7d77okDCjb7MeFJ0DcupqUoRiGjE39415HTfPgNc6R6BY9wt7SJsj4yOPBrIxHQVS8Yy6gZ3nZgsJ5rhcdkB6eCI6b3FJ31s6vsVcbVu5NBY8AF1qqjWLMazduISzEBwRDsofXfJjo1KLX59R410bmbrF5Z7QZfEfE/lettTWOyb4EgdhBoC3v0aLOfF6Bt12AFXDo2VGbgryceeOLAscp/Fr9ttH42hClBtWsxFU1N5dDENUsVHOwWcfCxd7aTtc0xjvaEYJWcZrRRZa1yrIvgeWaDk0LVxM5ePcT+ltdrymgmxmZYgxdiYC1qQDcNXDx9hN7yKeZDUztwGA0yl2iXW8aBXAy5hRnztR0TrREyOba26mUHxUJO7tfpIyOrpPbE0nR18vtCZ+inbvyqN9adpZhQPByG2XD9M6MoYdmBCc3Duv9qb+Ia0A8=</textarea>
	</form>
	```
