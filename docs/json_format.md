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

#### Properties

##### question_type
Must be set to "customer_enquire". 

##### answered 
Will be set to true upon submission. Used by Gramatica to tell which Intervention was submitted when there are multiple roles.

##### return_to_sender
Will be set to true if Intervention has been submitted from the return to sender modal.

##### forward 
Will be set to true if Intervention has been submitted from the forward modal.

##### unrecognised
Will be set to true if Intervention has been submitted by pressing the unrecognised button.

##### junk
Will be set to true if Intervention has been submitted by pressing the junk button.

##### reason
Descriptive text will appear at the top of the data entry section.

##### from_address
Sets from address in email forms. Is not user editable.

##### forward_address_options
Suggested to addresses for the forward modal. When list is not empty, the To label is replaced by a drop down menu.

##### return_to_sender_address_options
Suggested to addresses for the return to sender modal. When list is not empty, the To label is replaced by a drop down menu.

##### selected_forward_addresses
Addresses to email to when submitting from the forward modal. User editable.

##### selected_return_to_sender_addresses
Addresses to email to when submitting from the return to sender modal. User editable.

##### return_to_sender_email_subject
Subject for email when submitting from the return to sender modal. User editable.

##### forward_email_subject
Subject for email when submitting from the forward modal. User editable.

##### return_to_sender_email_body
Body for email when submitting from the return to sender modal. User editable.

##### forward_email_body
Body for email when submitting from the forward modal. User editable.


## Questions

### Text box

``` json
{
	"question_type": "text_box",
	"text": "Question text goes here",
	"value": "",
	"id": "question_01",
	"attributes" : { ... }
}
```

#### Properties

##### question_type 
Must be set as "text_box".

##### text
The label to be displayed to the left of the text box.

##### value
The text inside of the text box, editable by the user.

##### id
Not used in the front end, can be used in rules to identify a question.

##### attributes
Can be used to put custom html attributes on the text box. For more information see [here](/intervention_json_attributes.html).

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
	"value": "",
	"attributes": { ... }
}

