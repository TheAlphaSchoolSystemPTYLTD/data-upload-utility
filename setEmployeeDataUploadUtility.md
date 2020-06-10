**setEmployeeDataUploadUtility**
----
	Returns "success" and a count of updated employees, or a structure of invalid validations "__invalid" belonging to employee(s).

* **Version History:**

	TASS v53 - Added 2 new parameters `indig_status`, `main_activity`
	
	TASS v49.1 - Validations changed for `add1_text`, `city_text`, `state_text`, `post_code`, `country_text`, and `country_code` fields based on Single Touch Payroll

    TASS v48.0 - Method Added

* **Version:**

	2

* **Method:**

	`GET | POST`
	
*  **Params:**

	**Required:**
 
	`employees [array]` - Array of Employees to be updated

	`id [string]` - Employee Code

	**Optional:**
	
	`name_suffix [string]` - Name Suffix

	`position_text [string]` - Position Text

	`position_title [string]` - Position Title

	`school_email [string]` - School Email (Non Teachers only)

	`marital_stat_flag [string]` - Marital Status Flag (Must be a valid Marital Status)

	`birth_date [date dd/mm/yyyy or yyyy-mm-dd]` - Birth Date

	`driv_lic_text [string]` - Drivers Licence text

	`add2_text [string]` - Address Line 2

	`phone_h_text [string]` - Home Phone

	`phone_w_text [string]` - Home Phone

	`e_mail [string]` - Email

	`nok_name_text [string]` - Next of Kin Name

	`nok_relat_text [string]` - Next of Kin Relationship

	`nok_add1_text [string]` - Next of Kin Address Line 1

	`nok_add2_text [string]` - Next of Kin Address Line 2

	`nok_city_text [string]` - Next of Kin City

	`nok_state_text [string]` - Next of Kin State

	`nok_post_code [string]` - Next of Kin Post Code

	`nok_country_text [string]` - Next of Kin Country

	`nok_phone_h_text [string]` - Next of Kin Home Phone

	`nok_phone_w_text [string]` - Next of Kin Work Phone

	`ceider [string]` - Ceider

	**Conditional:**

	`add1_text [string]` - Address Line 1. Required if Payroll is enabled and it is an Australian School. If supplied length must be between 1 and 30 Characters.

	`city_text [string]` - City. Required if Payroll is enabled and it is an Australian School, if supplied length must be between 1 and 20 Characters.

	`state_text [string]` - State text. Required if post_code or country_text/country_code is present. 
	                        If supplied length must be between 1 and 3 Characters. 
							Where Payroll is enabled and it is an Australian School and Single Touch Payroll is not enabled, this field is required and valid values are 'QLD, NSW, VIC, TAS, SA, WA, NT, ACT, OTH'
							Where Single Touch Payroll is enabled, if Country is not specified this field is required and valid values are 'QLD, NSW, VIC, TAS, SA, WA, NT, ACT, AAT', otherwise if Country is not empty this field must be empty

	`post_code [string]` - Post Code. Required if state_text or country_text/country_code is present.
	                       If supplied length must be between 1 and 10 Characters.
						   Where Payroll is enabled and it is an Australian School and Single Touch Payroll is not enabled, this field is required and this value must be '9999' if state_code = 'OTH'
						   Where Single Touch Payroll is enabled, if Country is not specified this field is required and must be a numeric value in the range 0200 to 9999, otherwise if Country is not empty this field must be empty

	`country_text [string]` - Country. Required if state_text or post_code is present.
							  If supplied length must be between 1 and 20 Characters.
							  This field will only be available when Single Touch Payroll is not enabled.
							  Where Payroll is enabled and it is an Australian School: where state_code = 'OTH' this field is required.
							  Where Payroll is enabled and it is an Australian School: where state_code != 'OTH' this field is required but must be empty.

	`country_code [string]` - Country. Required if state_text or post_code is present.
							  If supplied length must be between 1 and 2 Characters.
							  This field will only be available when Single Touch Payroll is enabled.
							  Where State text is empty, this field is required and must be a valid country code.

	`mob_phone [string]` - Mobile Phone. Required if sms_flg is present. Where sms_flg = 'Y' the length must be between 1 and 10

	`sms_flg [string]` - SMS Flag (Y or N) Required if mob_phone is present. If supplied, length must be 1.

	`supervisor_code [string]` - Supervisor Code (Must be a valid employee code).  Required if supervisor2_code is present.

	`supervisor2_code [string]` - Supervisor 2 Code (Must be a valid employee code).  Required if supervisor_code is present.
	
	`indig_status [string]` - Indigenous Status Code (Must be a valid Indigenous Status code).  Required if indig_status is present.
	
	`main_activity [string]` - Main Activity Code (Must be a valid Activity code).  Required if main_activity is present.


* **Success Response:**

	```javascript
	"success": "You successfully saved 1 employee(s).",
	"employees": [
      {
        "supervisor_code": 1000016,
        "nok_city_text": "DEERAGUN",
        "COMPANYCODE": 10,
        "nok_phone_w_text": "0833669988",
        "position_title": "Operations Manager of Queensland",
        "supervisor2_code": 1000035,
        "nok_add2_text": "11 Test Ave",
        "position_text": "Operations",
        "add2_text": "10 Test Ave",
        "birth_date": "01/01/1984",
        "driv_lic_text": 123456789,
        "post_code": 4818,
        "id": 1000088,
        "nok_post_code": 8215,
        "ISPAYROLLENABLED": "YES",
        "country_text": "",
        "state_text": "QLD",
        "nok_name_text": "Jane Bloggs",
        "ceider": "ceid",
        "city_text": "TOWNSVILLE",
        "emp_code": 1000088,
        "add1_text": "Unit 1",
        "phone_h_text": "0745786258",
        "e_mail": "tester@example.com",
        "marital_stat_flag": "F",
        "nok_phone_h_text": "0812345687",
        "nok_add1_text": "Unit 2",
        "sms_flg": "Y",
        "phone_w_text": "0722556698",
        "nok_state_text": "WA",
        "nok_country_text": "BEL",
        "mob_phone": "0400007725",
        "name_suffix": "CertBus",
        "nok_relat_text": "Wife",
	"indig_status": "9",
	"main_activity": "1100"
      }
    ]
	```
 
* **Error Response:**

	Date `[field_name]` not a valid date
	```javascript
	__invalid: {
		"[field_name]": "Value is not a valid date."
	}
	```

	`employees` not supplied
	```javascript
	__invalid: {
		"employees": "'employees' is required"
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
		"employees":"Id must be unique for all rows."
	}
	```

	`id` not a valid employee code
	```javascript
	__invalid: {
		"id": "Invalid Employee Code"
	}
	```

	`name_suffix` exceed 30 characters
	```javascript
	__invalid: {
		"name_suffix": "exceeds 30 characters."
	}
	```

	`driv_lic_text` exceed 10 characters
	```javascript
	__invalid: {
		"driv_lic_text": "exceeds 10 characters."
	}
	```

	`position_text` exceed 20 characters
	```javascript
	__invalid: {
		"position_text": "exceeds 20 characters."
	}
	```

	`position_title` exceed 100 characters
	```javascript
	__invalid: {
		"position_title": "exceeds 100 characters."
	}
	```

	`school_email` exceed 60 characters
	```javascript
	__invalid: {
		"school_email": "exceeds 60 characters."
	}
	```

	`school_email` set for a Non Teacher
	```javascript
	__invalid: {
		"school_email": "'school_email' is allowed for Non Teachers only"
	}
	```

	`school_email` not in the correct format
	```javascript
	__invalid: {
		"school_email": "'school_email' is not valid"
	}
	```

	`supervisor_code` exceed 7 characters
	```javascript
	__invalid: {
		"supervisor_code": "exceeds 7 characters."
	}
	```

	`supervisor_code` is the same as the updating employee
	```javascript
	__invalid: {
		"supervisor_code": "An employee cannot be their own supervisor."
	}
	```

	`supervisor_code` and `supervisor2_code` are the same
	```javascript
	__invalid: {
		"supervisor_code": "supervisor_code and supervisor2_code must not be identical."
	}
	```

	`supervisor_code` is not supplied where 'supervisor2_code' is set
	```javascript
	__invalid: {
		"supervisor2_code": "supervisor_code' and 'supervisor2_code' must be submitted together"
	}
	```

	`supervisor2_code` is not supplied where 'supervisor_code' is set
	```javascript
	__invalid: {
		"supervisor_code": "supervisor_code' and 'supervisor2_code' must be submitted together"
	}
	```

	`supervisor_code` is empty where supervisor2_code is set
	```javascript
	__invalid: {
		"supervisor_code": "'supervisor_code' cannot be blank where the 'supervisor2_code' is used"
	}
	```

	`supervisor2_code` exceed 7 characters
	```javascript
	__invalid: {
		"supervisor2_code": "exceeds 7 characters."
	}
	```

	`supervisor2_code` is the same as the updating employee
	```javascript
	__invalid: {
		"supervisor2_code": "An employee cannot be their own supervisor."
	}
	```

	`marital_stat_flag` exceed 1 characters
	```javascript
	__invalid: {
		"marital_stat_flag": "exceeds 1 characters."
	}
	```

	`add1_text` exceed 30 characters
	```javascript
	__invalid: {
		"add1_text": "exceeds 30 characters."
	}
	```

	`add1_text` not supplied where Payroll is enabled and it is an Australian school.
	```javascript
	__invalid: {
		"add1_text": "add1_text is required"
	}
	```

	`add2_text` exceed 30 characters
	```javascript
	__invalid: {
		"add2_text": "exceeds 30 characters."
	}
	```

	`city_text` exceed 20 characters
	```javascript
	__invalid: {
		"city_text": "exceeds 20 characters."
	}
	```

	`city_text` not supplied where Payroll is enabled and it is an Australian school.
	```javascript
	__invalid: {
		"city_text": "city_text is required"
	}
	```

	`state_text` exceed 3 characters
	```javascript
	__invalid: {
		"state_text": "exceeds 3 characters."
	}
	```

	`state_text` not supplied where Payroll is enabled and it is an Australian school and Single Touch Payroll is not enabled.
	```javascript
	__invalid: {
		"state_text": "state_text is required"
	}
	```

	`state_text` not supplied when Single Touch Payroll is enabled and Country is empty
	```javascript
	__invalid: {
		"state_text": "state_text must be specified when country_code is empty"
	}
	```

	`state_text` not empty when Single Touch Payroll is enabled and Country is not empty
	```javascript
	__invalid: {
		"state_text": "state_text must be empty if country_code is specified"
	}
	```

	`state_text` is not of the following values where Payroll is enabled and it is an Australian school and Single Touch Payroll is not enabled 'QLD, NSW, VIC, TAS, SA, WA, NT, ACT, OTH'
	```javascript
	__invalid: {
		"state_text": "state_text is invalid"
	}
	```

	`state_text` or `post_code` or `country_text` is not supplied where at least one is present
	```javascript
	__invalid: {
		"state_text": "state_text is required if post_code or country_text are present"
	} 
	```

	`state_text` or `post_code` or `country_text` is not supplied where at least one is present
	```javascript
	__invalid: {
		"post_code": "post_code is required if state_code or country_text are present"
	} 
	```

	`state_text` or `post_code` or `country_text` is not supplied where at least one is present
	```javascript
	__invalid: {
		"country_text": "country_text is required if post_code or state_code are present"
	} 
	```

	`post_code` exceed 10 characters
	```javascript
	__invalid: {
		"post_code": "exceeds 10 characters."
	}
	```

	`post_code` not supplied where Payroll is enabled and it is an Australian school and Single Touch Payroll is not enabled.
	```javascript
	__invalid: {
		"post_code": "post_code is required"
	}
	```

	`post_code` not supplied when Single Touch Payroll is enabled and Country is empty
	```javascript
	__invalid: {
		"post_code": "post_code must be specified when country_code is empty"
	}
	```

	`post_code` not empty when Single Touch Payroll is enabled and Country is not empty
	```javascript
	__invalid: {
		"post_code": "post_code must be empty if country_code is specified"
	}
	```

	`post_code` is required where Payroll is enabled and it is an Australian school and Single Touch Payroll is not enabled. If state_code = 'OTH' then post_code must be '9999'
	```javascript
	__invalid: {
		"post_code": "post_code must be 9999 when state_code is OTH."
	}
	```

	`post_code` is required and must be a numeric value in the range 0200 to 9999 where Single Touch Payroll is enabled.
	```javascript
	__invalid: {
		"post_code": "post_code must be a numeric value in the range 0200 to 9999."
	}
	```

	`country_text` exceed 20 characters
	```javascript
	__invalid: {
		"country_text": "exceeds 20 characters."
	}
	```

	`country_text` is required where Payroll is enabled and it is an Australian school and Single Touch Payroll is not enabled and state_code is 'OTH'
	```javascript
	__invalid: {
		"country_text": "country_text cannot be empty or Australia when state_code is OTH."
	}
	```

	`country_text` is required where Payroll is enabled and it is an Australian school and Single Touch Payroll is not enabled and state_code is not 'OTH'
	```javascript
	__invalid: {
		"country_text": "country_text must be empty"
	}
	```

	`country_code` exceed 2 characters
	```javascript
	__invalid: {
		"country_code": "exceeds 2 characters."
	}
	```

	`country_code` is required when Single Touch Payroll is enabled and State text is empty
	```javascript
	__invalid: {
		"country_code": "country_code must be specified if state_text is empty"
	}
	```

	`country_code` is required and must be a valid country code when Single Touch Payroll is enabled and State text is empty
	```javascript
	__invalid: {
		"country_code": "country_code is invalid"
	}
	```

	`phone_h_text` exceed 30 characters
	```javascript
	__invalid: {
		"phone_h_text": "exceeds 30 characters."
	}
	```

	`phone_w_text` exceed 30 characters
	```javascript
	__invalid: {
		"phone_w_text": "exceeds 30 characters."
	}
	```

	`mob_phone` exceed 30 characters
	```javascript
	__invalid: {
		"mob_phone": "exceeds 30 characters."
	}
	```

	`sms_flg` exceed 1 characters
	```javascript
	__invalid: {
		"sms_flg": "exceeds 1 characters."
	}
	```

	`nok_name_text` exceed 30 characters
	```javascript
	__invalid: {
		"nok_name_text": "exceeds 30 characters."
	}
	```

	`nok_relat_text` exceed 20 characters
	```javascript
	__invalid: {
		"nok_relat_text": "exceeds 20 characters."
	}
	```

	`nok_add1_text` exceed 30 characters
	```javascript
	__invalid: {
		"nok_add1_text": "exceeds 30 characters."
	}
	```

	`nok_add2_text` exceed 30 characters
	```javascript
	__invalid: {
		"nok_add2_text": "exceeds 30 characters."
	}
	```

	`nok_city_text` exceed 20 characters
	```javascript
	__invalid: {
		"nok_city_text": "exceeds 20 characters."
	}
	```

	`nok_state_text` exceed 3 characters
	```javascript
	__invalid: {
		"nok_state_text": "exceeds 3 characters."
	}
	```

	`nok_post_code` exceed 10 characters
	```javascript
	__invalid: {
		"nok_post_code": "exceeds 10 characters."
	}
	```

	`nok_country_text` exceed 20 characters
	```javascript
	__invalid: {
		"nok_country_text": "exceeds 20 characters."
	}
	```

	`nok_phone_h_text` exceed 30 characters
	```javascript
	__invalid: {
		"nok_phone_h_text": "exceeds 30 characters."
	}
	```

	`nok_phone_w_text` exceed 30 characters
	```javascript
	__invalid: {
		"nok_phone_w_text": "exceeds 30 characters."
	}
	```

	`ceider` exceed 9 characters
	```javascript
	__invalid: {
		"ceider": "exceeds 9 characters."
	}
	```

	`marital_stat_flag` does not exist in the database
	```javascript
	__invalid: {
		"marital_stat_flag": "marital_stat_flag does not exist"
	} 
	```

	`e_mail` not in the correct format
	```javascript
	__invalid: {
		"e_mail": "e_mail is not valid"
	} 
	```

	`e_mail` exceed 60 characters
	```javascript
	__invalid: {
		"e_mail": "exceeds 60 characters."
	}
	```

	`mob_phone` or `sms_flg` is not supplied
	```javascript
	__invalid: {
		"mob_phone": "mob_phone and sms_flg must be submitted together"
	} 
	```

	`mob_phone` is not valid (where sms_flg = 'Y')
	```javascript
	__invalid: {
		"mob_phone": "mob_phone is not valid"
	} 
	```

	`sms_flg` must be Y or N
	```javascript
	__invalid: {
		"sms_flg": "sms_flg must be either Y or N"
	} 
	```
	
	`indig_status` exceed 1 characters
	```javascript
	__invalid: {
		"indig_status": "exceeds 1 characters."
	}
	```
		
	`main_activity` exceed 4 characters
	```javascript
	__invalid: {
		"main_activity": "exceeds 4 characters."
	}

* **Sample Parameters:**

	```javascript
	{
	"employees": [
		{
			"id": "1000088",
			"name_suffix":"CertBus",
			"position_text":"Operations",
			"position_title":"Operations Manager of Queensland",
			"supervisor_code":"1000016",
			"supervisor2_code":"1000035",
			"marital_stat_flag":"F",
			"birth_date":"01/01/1984",
			"driv_lic_text":"123456789",
			"add1_text":"Unit 1",
			"add2_text":"10 Test Ave",
			"city_text":"Townsville",
			"state_text":"QLD",
			"post_code":"4818",
			"country_text":"",
			"phone_h_text":"0745786258",
			"phone_w_text":"0722556698",
			"e_mail":"tester@example.com",
			"mob_phone":"0400007725",
			"sms_flg":"Y",
			"nok_name_text":"Jane Bloggs",
			"nok_relat_text":"Wife",
			"nok_add1_text":"Unit 2",
			"nok_add2_text":"11 Test Ave",
			"nok_city_text":"Deeragun",
			"nok_state_text":"WA",
			"nok_post_code":"8215",
			"nok_country_text":"BEL",
			"nok_phone_h_text":"0812345687",
			"nok_phone_w_text":"0833669988",
			"ceider":"ceid".
			"indig_status":"9",
			"main_activity":"1100"
		}
	]
	}
	```

* **Sample GET:** (With URL Encoded `token`)

	```HTML
	http://api.tasscloud.com.au/tassweb/api/?method=SetEmployeeDataUploadUtility&appcode=DEMOAP&company=10&v=2&token=BJVvYXC0We4Dtvp6Q49RqhBeAi6uqpTQ9t%2FKI9ZAFpCMeVXIFlDU5yNQIeYME%2BYLXgYA69RTUjXjLeVBetN6CaFMdPCKMWBXD%2Bkkt0%2Fuht0suYrSDONP6mx%2Fbt4WGgNOD5YoIYRNiIVDw2Qn2Oi5YodaEUgtGJohUJMzy3tqsX%2BraZk3j7d77okDCjb7MeFJ0DcupqUoRiGjE39415HTfPgNc6R6BY9wt7SJsj4yOPBrIxHQVS8Yy6gZ3nZgsJ5rhcdkB6eCI6b3FJ31s6vsVcbVu5NBY8AF1qqjWLMazduISzEBwRDsofXfJjo1KLX59R410bmbrF5Z7QZfEfE%2FlettTWOyb4EgdhBoC3v0aLOfF6Bt12AFXDo2VGbgryceeOLAscp%2FFr9ttH42hClBtWsxFU1N5dDENUsVHOwWcfCxd7aTtc0xjvaEYJWcZrRRZa1yrIvgeWaDk0LVxM5ePcT%2BltdrymgmxmZYgxdiYC1qQDcNXDx9hN7yKeZDUztwGA0yl2iXW8aBXAy5hRnztR0TrREyOba26mUHxUJO7tfpIyOrpPbE0nR18vtCZ%2BinbvyqN9adpZhQPByG2XD9M6MoYdmBCc3Duv9qb%2BIa0A8%3D
	```
	
* **Sample POST:**

	```HTML
	<form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
		 <input type="hidden" name="method" value="setEmployeeDataUploadUtility">
		 <input type="hidden" name="appcode" value="DEMOAP">
		 <input type="hidden" name="company" value="10">
		 <input type="hidden" name="v" value="2">
		 <textarea name="token">BJVvYXC0We4Dtvp6Q49RqhBeAi6uqpTQ9t/KI9ZAFpCMeVXIFlDU5yNQIeYME+YLXgYA69RTUjXjLeVBetN6CaFMdPCKMWBXD+kkt0/uht0suYrSDONP6mx/bt4WGgNOD5YoIYRNiIVDw2Qn2Oi5YodaEUgtGJohUJMzy3tqsX+raZk3j7d77okDCjb7MeFJ0DcupqUoRiGjE39415HTfPgNc6R6BY9wt7SJsj4yOPBrIxHQVS8Yy6gZ3nZgsJ5rhcdkB6eCI6b3FJ31s6vsVcbVu5NBY8AF1qqjWLMazduISzEBwRDsofXfJjo1KLX59R410bmbrF5Z7QZfEfE/lettTWOyb4EgdhBoC3v0aLOfF6Bt12AFXDo2VGbgryceeOLAscp/Fr9ttH42hClBtWsxFU1N5dDENUsVHOwWcfCxd7aTtc0xjvaEYJWcZrRRZa1yrIvgeWaDk0LVxM5ePcT+ltdrymgmxmZYgxdiYC1qQDcNXDx9hN7yKeZDUztwGA0yl2iXW8aBXAy5hRnztR0TrREyOba26mUHxUJO7tfpIyOrpPbE0nR18vtCZ+inbvyqN9adpZhQPByG2XD9M6MoYdmBCc3Duv9qb+Ia0A8=</textarea>
	</form>
	```
