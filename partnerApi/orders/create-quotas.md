
# Create Quote

## Path
/v1/quote/create

## Method

POST

## Headers

[require request context](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/authentication.md#request-context)

## Scope
quotas:create

## Body
Create Customer Quote Request
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| customerQuote | * | [Quote](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/create-quotas.md#quote) object |  | Customer quote object serialized as JSON. |
| referenceId |  | string | max 64 | Id of quote in external system. |

## Valid Request
```
{
	"referenceId": "87",
	"customerQuote": {
		"responseTime": "ThreeDays",
		"customerId": "424726",
		"shippingPrice": 10,
		"shippingTax": 1,
		"shippingDiscount": 2,
		"handlingFee": 3,
		"billing": {
			"firstName": "John",
			"lastName": "Doe",
			"zip": "11122",
			"country": "US",
			"state": "NY",
			"city": "New York",
			"address1": "some st, 15"
		},
		"shipping": {
			"firstName": "John",
			"lastName": "Doe",
			"zip": "11122",
			"country": "US",
			"state": "NY",
			"city": "New York",
			"address1": "some st, 15"
		},
		"items": [
			{
				"productId": "17",
				"mpn": "SCW103N",
				"itemName": "Satin Anodized Cashier Window Unit",
				"quantity": 3,
				"unitOfMeasure": {
					"id": "17"
				},
				"unitPrice": 10,
				"unitCost": 4,
				"unitWeight": 113,
				"tax": 2,
				"discount": 1,
			}
		],
		"total": 43
	}
}
```

## Success Response

HTTP Status Code: 200

Example:
```
{
    "submissionId": "351acbf8-2030-41b3-a0ea-0792236b5174"
}
```

## Error Response


| HTTP status code | Message |
|--|--|
| 400 | One or more validation errors occurred. |
| 500 | System error. |
|  |  |

Example for 400:
```
{
    "status": 400,
    "title": "One or more validation errors occurred.",
    "traceId": "0dc30f18-e6c9-45f9-b797-4d0c91401acc",
    "errors": {
        "items[0].unitCost": [
            "'unit Cost' must not be empty."
        ]
    }
}
```

Example for 500:
```
{
    "status": 500,
    "title": "System error.",
    "traceId": "d7234748-ba00-4d87-8cf2-246423cc172c"
}
```

# Quote operation status

## Path
/v1/quote/status

## Method

POST

## Headers

[require request context](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/authentication.md#request-context)


## Scope
quotas:status

## Body

SubmissionId serialized as json.

| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| SubmissionId | * | string | max 64 | Identifier of operation received at create or update response. |

## Valid Request
```
{
    "submissionId": "32e6a31b-f48a-4b9f-ab36-fdcda6dda461"
}
```

## Response

| Field | Description |
|--|--|
| quoteId | Identifier of quote. |
| status | [Status of operation](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/create-quotas.md#statuses). |
| errors | Array of errors strings. |
| payload | Quote data. The same as [get quote response](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#get-quotas). |
| referenceId |  Id of quote in external system. |

## Success Response

HTTP Status Code: 200

Example:
```
{
    "quoteId": "643543",
    "status": "Succeeded",
    "errors": null,
    "referenceId":"562875",
    "payload": {
        "quoteId": "643543",
        "orderIds": [],
        "createdAt": "2023-08-09T11:53:30",
        "total": 43.0,
        "currency": "USD",
        "status": "New Web Quotes Inquiry",
        "statusId": "22",
        "type": "Quotes",
        "typeId": "2",
        "customerId": "424726",
        "customerNotes": "Requested Response Time: Three Days\nId: 17, Product: Satin Anodized Cashier Window Unit\nQty: 3\nPrice: 10\nWeight: 113\nLine Comment: \n\n\n",
        "channel": null,
        "shippingMethod": null,
        "shippingPrice": 10.0,
        "shippingTax": 1.0,
        "shippingDiscount": -2.0,
        "handlingFee": 3.0,
        "createdBy": {
            "id": "93",
            "name": "Andrew Muhin"
        },
        "salesRep": {
            "id": "93",
            "name": "Andrew Muhin"
        },
        "billing": {
            "firstName": "John",
            "lastName": "Doe",
            "company": "",
            "phone": "4047027116",
            "altPhone": "",
            "fax": "",
            "zip": "11122",
            "country": "US",
            "state": "NY",
            "city": "New York",
            "address1": "some st, 15",
            "address2": "",
            "email": "johndoe@somesite.com"
        },
        "shipping": {
            "firstName": "John",
            "lastName": "Doe",
            "company": "",
            "phone": "4047027116",
            "altPhone": "",
            "fax": "",
            "zip": "11122",
            "country": "US",
            "state": "NY",
            "city": "New York",
            "address1": "some st, 15",
            "address2": "",
            "email": "johndoe@somesite.com"
        },
        "items": [
            {
                "itemId": "1784378",
                "productId": "17",
                "unitPrice": 10.0,
                "unitCost": 5.0,
                "quantity": 3,
                "linePosition": 1,
                "lineComment": null,
                "unitWeight": 113,
                "tax": 2.0,
                "discount": -1.0,
                "mpn": "SCW103N",
                "itemName": "Satin Anodized Cashier Window Unit",
                "productImage": "https://dkhtest.blob.core.windows.net/images/78559/original/SCW103N_2.gif",
                "productUrl": "https://www.dkhardware.com/satin-anodized-cashier-window-unit-scw103n-product-17.html",
                "unitOfMeasure": {
                    "id": "17",
                    "name": "Each"
                }
            }
        ],
        "notes": [
            {
                "noteId": "1622092",
                "author": {
                    "id": "93",
                    "name": "Andrew Muhin"
                },
                "message": "Additional comments: Requested Response Time: Three Days",
                "createdAt": "2023-08-09T11:53:31",
                "actionTypeCode": "QuestionToSupport"
            }
        ],
        "payments": null,
        "shipments": null
    }
}
```

Example with errors messages:
```
{
    "quoteId": null,
    "status": "Failed",
    "errors": [
        "Same reference ID already was used for another quote or in another request"
    ]
}
```
### Statuses

| Status | Description |
|--|--|
| Accepted | Submission accepted, but processing has not started yet. |
| Processing | Processing started. |
| Succeeded | Processed succeeded. | 
| Failed | Processed failed. | 

## Error Response

| HTTP status code | Message |
|--|--|
| 500 | System error. |
|  |  |

Example for 500:
```
{
    "status": 500,
    "title": "System error.",
    "traceId": "e65230db-a1ae-44d4-a303-23c4cf8c13bf"
}
```
# Contracts

## Quote

| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| customerId | * | string | max 64  | Customer's identifier |
| customerNotes | | string | max 8000 | Customer's notes or Cutting instructions |
| shippingPrice | * | money  |  | Shipping price |
| shippingTax | * | money  |  | Shipping tax |
| shippingDiscount | | money  | default(0) | Shipping discount |
| handlingFee | | money  | default(0) | Handling fee|
| total | * | money |  | Order total |
| billing | * | fields from [Address](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#address) |  | Billing address |
| shipping | * | fields from [Address](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#address) |  | Shipping address |
| items |  | array of [Quote Item](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/create-quotas.md#quote-item) |  | Items for quote |
| сomment |  | string | max 1000 | Quote operator comment. |
| responseTime |  | [Response Time](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/create-quotas.md#response-time) enum | | Expected response time for quote. |
| paymentMethodCode | * | string  | code from [Dictionary](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/dictionaries.md#payment-method) | Code of Payment method |

## Quote Item
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| itemId | * | string  | max 64 |  Item identifier |
| productId | * | string  | max 64 |  Product identifier |
| unitPrice | * | money |  | Product unit price |
| unitCost | * | money |  | Product unit price |
| unitWeight | * | float |  | Product weight |
| unitOfMeasure | * | [UnitOfMeasure](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#unit-of-measure) |  | Unit of measure. |
| quantity | * | integer |  | Product quantity in order line |
| linePosition | * | integer | sequence from 1..1000 unique for each item | Position of item line |
| tax | * | money   | default(0) | Total line tax |
| discount | * | money   | default(0) | Total line discount |
| mpn | * | string | max 50 | Manufacturer part number |
| itemName | * | string | max 2000 | Item name |


## Response Time

| Enum Value | Description |
|--|--|
| Unknown | Response time is unknown. Use any response time. |
| OneDay | Response time is 1 day. |
| ThreeDays | Response time is 3 days. |
| FiveDays | Response time is 5 days. |


# Events

## Quote Changed

### Id
customer-quote:changed

### Payload
| Field | Type | Description |
|--|--|--|
| quoteIds | Array of string | Identifiers of changed quotas.  |
| date |  date and time | UTC date of changes. |

Example:
```
{
	"event": "customer-quote:changed",
	"secret": "78f1a65ff4cc4d8ab6b855cd3c15ff79",
	"payload": {
		"quoteIds": [
			"6781345",
			"6781346"
		],
		"date":"2023-01-20T10:45:15Z"
	}
}
```

# Releases
-------------------------------
| Date | Version |
|--|--|
| 2023 January 20 | 20230120.2 |
### Release Notes
* Create customer quote endpoint added.
-------------------------------
| Date | Version |
|--|--|
| 2023 February 03 | 20230203.1 |
### Release Notes
* Create quote endpoint. Add validation for items collection. Items must not be empty.
-------------------------------
| Date | Version |
|--|--|
| 2023 Aug 09 | 20230809.1 |
### Release Notes
* Add line position field for quote items.
-------------------------------
| Date | Version |
|--|--|
| 2023 September 22 | 20230922.1 |
### Release Notes
* Add payment method code.
-------------------------------
| Date | Version |
|--|--|
| 2023 October 12 | 20231012.2 |
### Release Notes
* ReferenceId field added to status response near payload.
-------------------------------
| Date | Version |
|--|--|
| 2023 October 13 | 20231013.1 |
### Release Notes
* Items is not required for create quote.
-------------------------------
