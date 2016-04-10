# Intervention sample JSON

## Minumum required

This is the minimum required JSON to parse as a Customer Enquire. If you try this, you will see an error message saying "There were no enquiries or completions in this form.". To see something meaningful, add to the `questions` or `completion` properties. 

```json
{
	"question_type": "customer_enquire",
	"name": "",
	"answered": false,
	"role": "cloudtrade",
	"reason": "",
	"from_address": "something@something.com",
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
	"questions": [],
	"completion": {}
}				
```

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

#### Rows

#### Cells


## Full sample

```json
{
  "question_type": "customer_enquire",
  "name": "myform",
  "answered": false,
  "role": "cloudtrade",
  "reason": "Hilti Test",
  "from_address": "gramatica.test12@gmail.com",
  
  "return_to_sender": false,
  "forward": false,
  "unrecognised": false,
  "junk": false,
  "forward_address_options": [
    "richard.develyn@cloud-trade.com",
    "david.cocks@cloud-trade.com"
  ],
  "return_to_sender_address_options": [
  ],
  "selected_forward_addresses": ["something@something.com","something2@something.com"],
  "selected_return_to_sender_addresses":  ["something@something.com","something2@something.com"],
  "return_to_sender_email_subject": "",
  "forward_email_subject": "",
  "return_to_sender_email_body": "",
  "forward_email_body": "",
  "questions": [
    {
      "question_type": "drop_down_list",
      "text": "Special Processing?",
      "value": "",
      "id": "special",
      "options": [
        "No",
        "Manual",
        "OpenECX"                                                                                 
      ]
    },
    {
      "question_type": "drop_down_list",
      "text": "Country Codes for Manual Processing",
      "value": "",
      "id": "country",
      "options": [
        "UK",
        "US",
        "DE"
      ]
    },
    {
      "question_type": "text_box",
      "text": "Datey",
      "value": "",
      "id": "comments",
	  "attributes" : { 
		"type" : "date"
	  }
    }
  ],
  "completion": {
    "caption": "Invoice",
    "group": [
      {
        "caption": "Date",
        "name": "invoice_date",
        "value": "10/02/13"
      },
      {
        "caption": "Order Number",
        "name": "order_number",
        "value": "po12345",
		 "attributes": {
                  "required": "true"
                }
      },
      {
        "caption": "Customer",
        "group": [
          {
            "name": "buyer_contact",
            "caption": "Contact",
            "value": null
          },
          {
            "name": "buyer_party",
            "caption": "Name",
            "value": "DUPE VENDOR TEST"
          },
          {
            "min": 0,
            "max": 3,
            "caption": "Street",
            "name": "buyer_street",
            "value": [
              "46, benridge park",
              "newsham",
             "blyth"
            ]
          },
          {
            "name": "buyer_postcode",
            "caption": "Post Code",
            "value": "ne24 4tb"
          }
        ]
      },
      {
        "caption": "Delivery",
        "group": [
          {
            "name": "delivery_contact",
            "caption": "Contact",
            "value": null
          },
          {
            "min": 0,
            "max": 3,
            "name": "delivery_street",
            "caption": "Street",
            "value": []
          },
          {
            "name": "delivery_city",
            "caption": "City",
            "value": null
          },
          {
            "name": "delivery_postcode",
            "caption": "Post Code",
            "value": null
          }
        ]
      },
      {
        "caption": "Order Lines",
        "group": [
          {
            "caption": "Line",
            "min": 0,
            "max": 999,
            "line_template": [
              {
                "caption": "Item #",
                "name": "line_item",
                "type": "number",
                "value": null
              },
              {
                "caption": "Description",
                "name": "line_descr",
                "value": null
              },
              {
                "caption": "Quantity",
                "name": "line_quantity",
                "value": null
              },
              {
                "caption": "Unit Amount",
                "name": "line_unit_amount",
                "value": null
              },
              {
                "caption": "Vat",
                "attributes": {
                  "hidden": "hidden"
                },
                "name": "line_vat_amount",
                "value": null
              },
              {
                "caption": "Total",
                "attributes": {
                  "hidden": "hidden"
                },
                "name": "line_total_amount",
                "value": null
              },
              {
                "caption": "Net",
                "name": "line_net_amount",
                "value": null
              }
            ],
            "group": [
              {
                "line_item": "4002688",
                "line_descr": "MORPHY RICHARDS MANUAL",
                "line_quantity": "1",
                "line_unit_amount": "41.66",
                "line_vat_amount": "8.33",
                "line_total_amount": "49.99",
                "line_net_amount": "41.66"
              },
              {
                "line_item": "9810387",
                "line_descr": "HOME SHOP DELIVERY CHARGE",
                "line_quantity": "1",
                "line_unit_amount": "0",
                "line_vat_amount": "0",
                "line_total_amount": "0",
                "line_net_amount": "0"
              },
              {
                "line_item": "9810064",
                "line_descr": "HOME SHOP DELIVERY CHARGE",
                "line_quantity": "1",
                "line_unit_amount": "3.29",
                "line_vat_amount": "0.66",
                "line_total_amount": "3.95",
                "line_net_amount": "3.29"
              },
              {
                "line_item": "CLDISC",
                "line_descr": "Order Discount",
                "line_quantity": "1",
                "line_unit_amount": "-2.08",
                "line_vat_amount": "-0.42",
                "line_total_amount": "-2.5",
                "line_net_amount": "-2.08"
              }
            ]
          }
        ]
      },
      {
        "caption": "Total",
        "name": "total_net",
        "value": "42.87"
      },
      {
        "caption": "Total VAT",
        "attributes": {
          "style": "visibility: hidden;"
        },
        "name": "total_vat",
        "value": "8.57"
      },
      {
        "caption": "Total Gross",
        "hidden": "true",
        "name": "total_invoice",
        "value": "51.44"
      }
    ]
  },
  "return_to_sender_address": "richard.develyn@gmail.com"
}			
```