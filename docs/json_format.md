# Customer Enquire sample JSON

## Top level 

```json
{
	"question_type": "customer_enquire",
	"answered": false,
	"role": "cloudtrade",
	"reason": "",
	"long_reason": "",
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

All properties must exist for the form to validate correctly. The same applies to all of the JSON examples below. 

The `"question_type"` property must be set to `"customer_enquire"`. This is just for future proofing, in case we want to add more forms. 

All of the arrays take strings, except for `"questions"`. For example:

```json
{
	"forward_address_options": ["1@example.com", "2@example.com"]
}
```

`"answered"`, `"return_to_sender"`, `"forward"`, `"unrecognised"` and `"junk"` should all be initially set to false. When a form is submitted, `"answered"` will be set to `true` to inform Gramatica which form was submitted in the case that there are forms set up for multiple roles. If the form is submitted using the one of the buttons other than submit, the appropriate property will also be set to `true`.

`"completion"` takes an object that David Thompson has defined. The documentation for that hasn't been written yet.

## Questions

The `"questions"` array takes objects in the following formats.

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

The `"question_type"` property must be set to `"text_box"` to render a text box. The `"text"` property specifies the label that will be displayed to the left of the text box. The `"value"` property will be updated when a user enters text into the text box. It can be prepopulated by the rules writer. The `"id"` field isn't used in the front end, but provides a means of finding a question again for the rules writer. Click [here](#attributes) for attributes documentation.

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

The `question_type` property must be set to `drop_down_list` to render a drop down list. As with text boxes, `"text"` specifies the label and `"value"` stores the option selected by the user. It can be set by the rules writer to preselect an option. `"options"` specifies the options that the user can select from.

### Section

``` json
{	
	"question_type": "section",
	"title": "The section title"
	"questions": [ ... ]
}
```

Sections can be used to group questions together. The `"questions"` array works just like the array in the `customer_enquire` JSON. This means that sections are infinitely nestable. Try not to go too crazy.

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

The `"question_type"` property must be set to `"table"` to render a table. The `"headings"` array takes strings, these specify the table's headings. The `"rows"` array takes objects of the format below. 


#### Rows

``` json
{
	"question_type": "table_row",
	"cells": [ ... ]		
}
```

The `"question_type"` property must be set to `"table_row"`. The `"cells"` array takes objects of the format below.

#### Cells

``` json 
{
	"question_type": "table_cell",
	"editable": false,
	"value": "",
	"attributes": { ... }
}
```

Cells with `"editable"` set to `false` will display the value as normal text, cells with `"editable"` set to `false` will render a text box with `"value"` set to the contents of the text box. Attributes are only applied if `"editable"` is set to `true`. Click [here](#attributes) for attributes documentation.

#### Dropdown cells

``` json 
{
	"question_type": "table_cell_drop_down_list",
	"value": "Option 2",
	"options": [
	  "Option 1",
	  "Option 2",
      "Option 3"  
	]
}
```

Very similar to drop down list questions. Just without the `"text"`.

#### Popover cells

``` json 
{
	"question_type": "table_cell_popover",
	"text": "Put text here"
}
```

Will display the word "Details" in the table, hovering shows the text specified in `"text"`.

## Attributes 

All text boxes (not drop downs) have support for HTML attributes. We've not tested everything, and we may disable some things in future, so use cautiously.

If you want to explore the possibilities, you can read about HTML attributes [here](http://www.w3schools.com/tags/tag_input.asp) and [Here](http://www.w3schools.com/tags/ref_attributes.asp).

You can use as many attributes as you like, although some might override the functionality of others. For example, date pickers usually override placeholders. 

Attributes are specified like this, where the property names are the desired attributes, and the values their values. Assign this object to the `"attributes"` property of text box or table cell questions.

``` json
{
	"type": "date",
	"required": "required",
	"placeholder": "some placeholder text"
}
```

So far, attributes that we've looked at and have some level of confidence in are:

### Date pickers

``` json
{
	"type": "date"
}
```

Makes a date picker. Works in Chrome and Edge out of the box, we've added IE support, we thought it worked in Firefox out of the box but we've had reports of it not working inside tables in Firefox.

### Required fields

``` json
{
	"required": "required"
}
```

Will prevent submission of the form if the field is empty. Fields are coloured red until they contain a value, then green. We believe it works in all browsers.

### Recommended fields

``` json
{
	"recommended": "required"
}
```

Not a standard HTML attribute, but we've implemented it. Will colour fields yellow until they contain a value, and then green. Won't prevent submission.

Will prevent submission of the form if the field is empty. We believe it works in all browsers.

### Placeholder text

``` json
{
	"placeholder": "text goes here"
}
```

Will display this text inside the text box in light grey when the text box is empty.

### Testing/implementing more attributes

If anyone wants this list extended, please shout.



