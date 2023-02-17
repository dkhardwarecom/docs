
# Update Quote

## Path
/v1/quote/update

## Method

POST

## Headers

[require request context](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/authentication.md#request-context)

## Scope
quotes:update

## Body
Create Customer Quote Request
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| customerQuote | * | [Updatable Quote](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-quotes.md#updatable-quote) object |  | Customer quote data for update serialized as JSON. |
| referenceId |  | string | max 64 | Id of quote in external system. |

## Valid Request
```
{
	"customerQuote": {
		"quoteId": "629265",
		"quoteTotals": {
			"handlingFee": {
				"newValue": 12.3,
				"oldValue": 11.7
			}
		},
		"billingAddress": {
			"email": {
				"newValue": "johndoe@my--best-company.com",
				"oldValue": "johndoe@my-company.com"
			},
			"company": {
				"newValue": "My Best Company",
				"oldValue": "My Company"
			}
		},
		"shippingAddress": {
			"email": {
				"newValue": "johndoe@my-best-company.com",
				"oldValue": "johndoe@my-company.com"
			},
			"company": {
				"newValue": "My Best Company",
				"oldValue": "My Company"
			}
		}
	}
}
```

## Success Response

HTTP Status Code: 200

Example:
```
{
    "submissionId": "713ff825-3372-4de0-848a-accda64d4a0b"
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
    "traceId": "1e99f720-3f3c-47a5-aeb2-6226af64cd36",
    "errors": {
        "quoteTotals.handlingFee.NewValue": [
            "'handling Fee New Value' must be greater than or equal to '0'."
        ],
        "shippingAddress.email.NewValue": [
            "'email New Value' is not a valid email address."
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

Status operation is the same as [Quote operation status](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/create-quotes.md#quote-operation-status) for create quote operation.

# Contracts

## Updatable Quote

| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| quoteId | * | string  | max 64 |  Quote identifier|
| quoteTotals | | fields from [Updatable Quote Totals](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-quotes.md#updatable-quote-totals) |  | Quote totals data for update |
| billing | | fields from [Address](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#address) |  | Billing address |
| shipping | | fields from [Address](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#address) |  | Shipping address |
| items |  | array of [Quote Item](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-quotes.md#quote-item) |  | Items for quote |

## Updatable Quote Totals
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| shippingPrice |  | money [u](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-quotes.md#updatable-property)  | greater or equal than zero | Shipping price |


## Updatable Quote Address

| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| firstName | * | string | max 150 | First name |
| lastName | * | string | max 150 | Last name |
| company |  | string | max 250 | Company name |
| phone |  | string | max 50 | Phone number |
| altPhone | | string | max 50 | Alternative phone number |
| fax |  | string |  max 50 | Fax|
| zip | * | string | max 50 | Zip/Postal code |
| country | * | string | max 150 | Country name |
| state | * | string | max 50 | State or region |
| city | * | string | max 255 | City |
| address1 | * | string  | max 255 | Address line 1 |
| address2 |  | string  | max 255 | Address line 2 |
| email |  | string  | max 100|Email address|

## Quote Item
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| productId | * | string  | max 64 |  Product identifier|
| unitPrice | * | money |  | Product unit price |
| unitCost | * | money |  | Product unit price |
| unitWeight | * | float |  | Product weight |
| unitOfMeasure | * | [UnitOfMeasure]() |  | Unit of measure. |
| quantity | * | integer |  | Product quantity in order line |
| lineComment |  | string |  | Additional line comment |
| tax |  | money   | default(0) | Total line tax |
| discount |  | money   | default(0) | Total line discount |
| mpn |  | string | max 50 | Manufacturer part number |
| itemName |  | string | max 2000 | Item name |

## Response Time

| Enum Value | Description |
|--|--|
| Unknown | Response time is unknown. Use any response time. |
| OneDay | Response time is 1 day. |
| ThreeDays | Response time is 3 days. |
| FiveDays | Response time is 5 days. |

## Updatable Property
| Property | Description |
|--|--|
| newValue | New value to update. |
| oldValue | Old value to handle concurrent updates. |


# Events

## Quote Changed

### Id
customer-quote:changed

### Payload
| Field | Type | Description |
|--|--|--|
| quoteIds | Array of string | Identifiers of changed quotes.  |
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

