# Intervention sample JSON

## Top level 

```json
{
	"question_type": "customer_enquire",
	"answered": false,
	"role": "cloudtrade",
	"reason": "",
	"from_address": "",
	"return_to_sender": false,
	"forward": false,
	"unrecognised": false,
	"junk": false,
	"forward_address_options": [],
	"return_to_sender_address_options": [],
	"selected_forward_addresses": [],
	"selected_return_to_sender_addresses":  [],
	"return_to_sender_email_subject": "",
	"forward_email_subject": "",
	"return_to_sender_email_body": "",
	"forward_email_body": "",
	"questions": [ ... ],
	"completion": { ... }
}				
```

### Properties

| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |



## Questions

### Text box

``` json
{
	"question_type": "text_box",
	"text": "Question text goes here",
	"value": "",
	"id": "question_01"
}
```

### Drop down box

``` json
{
	"question_type": "drop_down_list",
	"text": "Question text goes here",
	"value": "",
	"id": "question_01",
	"options": [
		"Option 1",
		"Option 2",
		"Option 3"                                                                                 
	]
}
```

### Table

``` json
{
	"question_type": "table",
	"headings": [
		"Heading 1",
		"Heading 2",
		"Heading 3"
	],
	"rows": [ ... ]
			
}
```

#### Rows

``` json
{
	"question_type": "table_row",
	"cells": [ ... ]		
}
```

#### Cells

``` json 
{
	"question_type": "table_cell",
	"editable": false,
	"value": ""
}

