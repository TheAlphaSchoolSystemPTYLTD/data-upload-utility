**setStudentDataUploadUtility**
----
	Returns "success" and a count of updated students, or a structure of invalid validations "__invalid" belonging to student(s).

* **Version:**

	2

* **Method:**

	`GET | POST`
	
*  **Params:**

	**Required:**
 
	`students [array]` - Array of Students to be updated

	`id [string]` - Student Code

	**Optional:**
	
	`usi [alphanumeric]` - USI (No spaces or special chars)

	`alt_id [string]` - Alt ID (Must be a unique value against any student in the database and the submitted list)

	`form_cls [alphanumeric]` - Form Class (No spaces or special chars)

	`fte [decimal (1,2)]` - FTE (Range 0.00 to 1.00 only)

	`house [string]` - House (Must be an existing House)

	`religion [string]` - Religion (Must be an existing Religion)

	`pctut_grp [alphanumeric]` - PC Tut Group (No spaces or special chars)

	`campus_code [string]` - Campus (Must be an existing Campus)

	`prev_school [string]` - Previous School (Must be an existing Feed Scool)

	`e_mail [string]` - E Mail

	`resident_sts [string]` - Resident Status (Must be an existing Resident Status)

	`visa_expiry [date dd/mm/yyyy or yyyy-mm-dd]` - Visa Expiry

	`visa_subclass [string]` - Visa Subclass

	`date_arrival [date dd/mm/yyyy or yyyy-mm-dd]` - Date of Arrival

	`sud1_flg [string]` to `sud10_flg [string]` - User Defined Flags

	`sud11_code [string]` to `sud20_code [string]` - User Defined Codes (Must be an existing UD Code)

	`sud21_text [string]` to `sud25_text [string]` - User Defined Text

	`sud26_bill [string]` to `sud30_bill [string]` - User Defined Billing text

	`ceider [string]` - Ceider

	**Conditional:**

	`surname [string]` - Surname. If supplied, length must be between 1 and 30 Characters

	`given_name [string]` - Given Name. If supplied, length must be between 1 and 30 Characters

	`preferred_name [string]` - Preferred Name. If supplied, length must be between 1 and 20 Characters

	`mob_phone [string]` - Mobile Phone. Required if sms_flg is present.

	`sms_flg [string]` - SMS Flag (Y or N) Required if mob_phone is present. If supplied, length must be 1.


* **Success Response:**

	```javascript
	"success": "You successfully saved 1 student(s).",
	"students": [
      {
        "resident_sts": "PR",
        "sud28_bill": "My bill",
        "alt_id": "001125",
        "sud4_flg": "N",
        "pctut_grp": "ABC",
        "preferred_name": "Eli",
        "id": "0010091",
        "house": "BA",
        "surname": "Bailey-Farrell",
        "given_name": "Elias Isaak",
        "ceider": "DIDE",
        "usi": 1009110,
        "sud11_code": "ORG",
        "e_mail": "bradley.fleming@tassweb.com.au",
        "date_arrival": "02/07/2014",
        "sud22_text": "001256",
        "campus_code": "SE",
        "sms_flg": "N",
        "stud_code": "0010091",
        "religion": "LU",
        "visa_subclass": "subvis",
        "fte": 0.8,
        "prev_school": "STJ",
        "form_cls": "B",
        "mob_phone": "0400000097",
        "visa_expiry": "01/8/2019"
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
	
	Decimal `[field_name]` not a valid decimal
	```javascript
	__invalid: {
		"[field_name]": "Value is not a valid decimal."
	}
	```


	`students` not supplied
	```javascript
	__invalid: {
		"students": "'students' is required"
	}
	```

	`id` not supplied
	```javascript
	__invalid: {
		"id": "Id is required for all rows."
	}
	```

	`surname` length less than 1
	```javascript
	__invalid: {
		"surname": "surname is required"
	}
	```

	`given_name` length less than 1
	```javascript
	__invalid: {
		"given_name": "given_name is required"
	}
	```

	`preferred_name` length less than 1
	```javascript
	__invalid: {
		"preferred_name": "preferred_name is required"
	}
	```

	`id` not a valid student code
	```javascript
	__invalid: {
		"id": "Invalid Student Code"
	}
	```

	`surname` exceed 30 characters
	```javascript
	__invalid: {
		"surname": "The value for this field exceeds the length permitted (NN of 30)."
	} 
	```

	`given_name` exceed 30 characters
	```javascript
	__invalid: {
		"given_name": "The value for this field exceeds the length permitted (NN of 30)."
	} 
	```

	`preferred_name` exceed 20 characters
	```javascript
	__invalid: {
		"preferred_name": "The value for this field exceeds the length permitted (NN of 20)."
	} 
	```

	`usi` exceed 10 characters
	```javascript
	__invalid: {
		"usi": "The value for this field exceeds the length permitted (NN of 10)."
	} 
	```

	`usi` contains invalid characters (other than A-Z and 0-9)
	```javascript
	__invalid: {
		"usi": "Value is not a valid alphanumeric code."
	} 
	```

	`alt_id` exceed 40 characters
	```javascript
	__invalid: {
		"alt_id": "The value for this field exceeds the length permitted (NN of 40)."
	} 
	```

	`alt_id` is not unique in the database or supplied list of students
	```javascript
	__invalid: {
		"alt_id": "Value is not unique"
	} 
	```

	`form_cls` exceed 1 characters
	```javascript
	__invalid: {
		"form_cls": "The value for this field exceeds the length permitted (NN of 1)."
	} 
	```

	`form_cls` contains invalid characters (other than A-Z and 0-9)
	```javascript
	__invalid: {
		"form_cls": "Value is not a valid alphanumeric code."
	} 
	```

	`house` exceed 2 characters
	```javascript
	__invalid: {
		"house": "The value for this field exceeds the length permitted (NN of 2)."
	} 
	```

	`house` does not exist in the database
	```javascript
	__invalid: {
		"house": "house does not exist"
	} 
	```

	`religion` exceed 2 characters
	```javascript
	__invalid: {
		"religion": "The value for this field exceeds the length permitted (NN of 2)."
	} 
	```

	`religion` does not exist in the database
	```javascript
	__invalid: {
		"religion": "religion does not exist"
	} 
	```

	`pctut_grp` exceed 5 characters
	```javascript
	__invalid: {
		"pctut_grp": "The value for this field exceeds the length permitted (NN of 5)."
	} 
	```

	`pctut_grp` contains invalid characters (other than A-Z and 0-9)
	```javascript
	__invalid: {
		"pctut_grp": "Value is not a valid alphanumeric code."
	} 
	```

	`campus_code` exceed 3 characters
	```javascript
	__invalid: {
		"campus_code": "The value for this field exceeds the length permitted (NN of 3)."
	} 
	```

	`campus_code` does not exist in the database
	```javascript
	__invalid: {
		"campus_code": "campus does not exist"
	} 
	```

	`prev_school` exceed 5 characters
	```javascript
	__invalid: {
		"prev_school": "The value for this field exceeds the length permitted (NN of 5)."
	} 
	```

	`prev_school` does not exist in the database
	```javascript
	__invalid: {
		"prev_school": "prev_school does not exist"
	} 
	```

	`e_mail` exceed 60 characters
	```javascript
	__invalid: {
		"e_mail": "The value for this field exceeds the length permitted (NN of 60)."
	} 
	```

	`e_mail` not in the correct format
	```javascript
	__invalid: {
		"e_mail": "e_mail is not valid"
	} 
	```

	`mob_phone` exceed 30 characters
	```javascript
	__invalid: {
		"mob_phone": "The value for this field exceeds the length permitted (NN of 30)."
	} 
	```

	`mob_phone` or `sms_flg` is not supplied
	```javascript
	__invalid: {
		"mob_phone": "mob_phone and sms_flg must be submitted together"
	} 
	```

	`sms_flg` exceed 1 characters
	```javascript
	__invalid: {
		"sms_flg": "The value for this field exceeds the length permitted (NN of 1)."
	} 
	```

	`resident_sts` exceed 3 characters
	```javascript
	__invalid: {
		"resident_sts": "The value for this field exceeds the length permitted (NN of 3)."
	} 
	```

	`visa_subclass` exceed 6 characters
	```javascript
	__invalid: {
		"visa_subclass": "The value for this field exceeds the length permitted (NN of 6)."
	} 
	```

	`ceider` exceed 9 characters
	```javascript
	__invalid: {
		"ceider": "The value for this field exceeds the length permitted (NN of 9)."
	} 
	```

	`fte` has more than 2 decimal points
	```javascript
	__invalid: {
		"fte": "Value has more than 2 decimal points."
	}
	```

	`sud1_flg [string]` to `sud10_flg [string]` exceed 1 character
	```javascript
	__invalid: {
		"[field]": "The value for this field exceeds the length permitted (NN of 1)."
	} 
	```

	`sud11_code [string]` to `sud20_code [string]` exceed 3 characters
	```javascript
	__invalid: {
		"[field]": "The value for this field exceeds the length permitted (NN of 3)."
	} 
	```

	`sud11_code [string]` to `sud20_code [string]` does not exist in the database
	```javascript
	__invalid: {
		"[field]": "[field] does not exist"
	} 
	```

	`sud21_text [string]` to `sud25_text [string]` exceed 20 characters
	```javascript
	__invalid: {
		"[field]": "The value for this field exceeds the length permitted (NN of 20)."
	} 
	```

	`sud26_bill [string]` to `sud30_bill [string]` exceed 8 characters
	```javascript
	__invalid: {
		"[field]": "The value for this field exceeds the length permitted (NN of 20)."
	} 
	```

* **Sample Parameters:**

	```javascript
	{
		"students": [
	      {
	        "resident_sts": "PR",
	        "sud28_bill": "My bill",
	        "alt_id": "001125",
	        "sud4_flg": "N",
	        "pctut_grp": "ABC",
	        "preferred_name": "Eli",
	        "id": "0010091",
	        "house": "BA",
	        "surname": "Bailey-Farrell",
	        "given_name": "Elias Isaak",
	        "ceider": "DIDE",
	        "usi": 1009110,
	        "sud11_code": "ORG",
	        "e_mail": "bradley.fleming@tassweb.com.au",
	        "date_arrival": "02/07/2014",
	        "sud22_text": "001256",
	        "campus_code": "SE",
	        "sms_flg": "N",
	        "religion": "LU",
	        "visa_subclass": "subvis",
	        "fte": 0.8,
	        "prev_school": "STJ",
	        "form_cls": "B",
	        "mob_phone": "0400000097",
	        "visa_expiry": "01/8/2019"
	      }
	    ]
	}
	```

* **Sample GET:** (With URL Encoded `token`)

	```HTML
	http://api.tasscloud.com.au/tassweb/api/?method=SetStudentDataUploadUtility&appcode=DEMOAP&company=10&v=2&token=BJVvYXC0We4Dtvp6Q49RqhBeAi6uqpTQ9t%2FKI9ZAFpCMeVXIFlDU5yNQIeYME%2BYLXgYA69RTUjXjLeVBetN6CaFMdPCKMWBXD%2Bkkt0%2Fuht0suYrSDONP6mx%2Fbt4WGgNOD5YoIYRNiIVDw2Qn2Oi5YodaEUgtGJohUJMzy3tqsX%2BraZk3j7d77okDCjb7MeFJ0DcupqUoRiGjE39415HTfPgNc6R6BY9wt7SJsj4yOPBrIxHQVS8Yy6gZ3nZgsJ5rhcdkB6eCI6b3FJ31s6vsVcbVu5NBY8AF1qqjWLMazduISzEBwRDsofXfJjo1KLX59R410bmbrF5Z7QZfEfE%2FlettTWOyb4EgdhBoC3v0aLOfF6Bt12AFXDo2VGbgryceeOLAscp%2FFr9ttH42hClBtWsxFU1N5dDENUsVHOwWcfCxd7aTtc0xjvaEYJWcZrRRZa1yrIvgeWaDk0LVxM5ePcT%2BltdrymgmxmZYgxdiYC1qQDcNXDx9hN7yKeZDUztwGA0yl2iXW8aBXAy5hRnztR0TrREyOba26mUHxUJO7tfpIyOrpPbE0nR18vtCZ%2BinbvyqN9adpZhQPByG2XD9M6MoYdmBCc3Duv9qb%2BIa0A8%3D
	```
	
* **Sample POST:**

	```HTML
	<form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
		 <input type="hidden" name="method" value="setStudentDataUploadUtility">
		 <input type="hidden" name="appcode" value="DEMOAP">
		 <input type="hidden" name="company" value="10">
		 <input type="hidden" name="v" value="2">
		 <textarea name="token">BJVvYXC0We4Dtvp6Q49RqhBeAi6uqpTQ9t/KI9ZAFpCMeVXIFlDU5yNQIeYME+YLXgYA69RTUjXjLeVBetN6CaFMdPCKMWBXD+kkt0/uht0suYrSDONP6mx/bt4WGgNOD5YoIYRNiIVDw2Qn2Oi5YodaEUgtGJohUJMzy3tqsX+raZk3j7d77okDCjb7MeFJ0DcupqUoRiGjE39415HTfPgNc6R6BY9wt7SJsj4yOPBrIxHQVS8Yy6gZ3nZgsJ5rhcdkB6eCI6b3FJ31s6vsVcbVu5NBY8AF1qqjWLMazduISzEBwRDsofXfJjo1KLX59R410bmbrF5Z7QZfEfE/lettTWOyb4EgdhBoC3v0aLOfF6Bt12AFXDo2VGbgryceeOLAscp/Fr9ttH42hClBtWsxFU1N5dDENUsVHOwWcfCxd7aTtc0xjvaEYJWcZrRRZa1yrIvgeWaDk0LVxM5ePcT+ltdrymgmxmZYgxdiYC1qQDcNXDx9hN7yKeZDUztwGA0yl2iXW8aBXAy5hRnztR0TrREyOba26mUHxUJO7tfpIyOrpPbE0nR18vtCZ+inbvyqN9adpZhQPByG2XD9M6MoYdmBCc3Duv9qb+Ia0A8=</textarea>
	</form>
	```
