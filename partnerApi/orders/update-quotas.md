
# Update Quote

## Path
/v1/quote/update

## Method

POST

## Headers

[require request context](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/authentication.md#request-context)

## Scope
quotas:update

## Body
Update Customer Quote Request
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| customerQuote | * | [Updatable Quote](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-quotas.md#updatable-quote) object |  | Customer quote data for update serialized as JSON. |


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
		"billing": {
			"email": {
				"newValue": "johndoe@my--best-company.com",
				"oldValue": "johndoe@my-company.com"
			},
			"company": {
				"newValue": "My Best Company",
				"oldValue": "My Company"
			}
		},
		"shipping": {
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

Status operation is the same as [Quote operation status](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/create-quotas.md#quote-operation-status) for create quote operation.

# Contracts

## Updatable Quote

| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| quoteId | * | string  | max 64 |  Quote identifier|
| quoteTotals |  | fields from [Updatable Quote Totals](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-quotas.md#updatable-quote-totals) |  | Quote totals data for update |
| billing |  | fields from [Updatable Quote Address](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-quotas.md#updatable-quote-address) |  | Billing address |
| shipping |  | fields from [Updatable Quote Address](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-quotas.md#updatable-quote-address) |  | Shipping address |
| items |  | fields from [Updatable Quote Items](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-quotas.md#updatable-quote-items) |  | Items for update |
| notes |  | fields from [Updatable Notes](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-quotas.md#updatable-notes) |  | Notes for update |

## Updatable Quote Totals
All properties are [Updatable](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-quotas.md#updatable-property)

| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| shippingPrice |  | money  | greater or equal than zero | Shipping price |
| shippingTax |  | money  | greater or equal than zero | Shipping tax |
| shippingDiscount |  | money  | greater or equal than zero | Shipping discount |
| handlingFee |  | money  | greater or equal than zero | Handling fee |


## Updatable Quote Address
All properties are [Updatable](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-quotas.md#updatable-property)

| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| email |  | string  | max 100|Email address|
| firstName |  | string | max 150 | First name |
| lastName |  | string | max 150 | Last name |
| company |  | string | max 250 | Company name |
| phone |  | string | max 50 | Phone number |
| altPhone | | string | max 50 | Alternative phone number |
| fax |  | string |  max 50 | Fax|
| zip |  | string | max 50 | Zip/Postal code |
| country |  | string | max 150 | Country name |
| state |  | string | max 50 | State or region |
| city |  | string | max 255 | City |
| address1 |  | string | max 255 | Address line 1 |
| address2 |  | string  | max 255 | Address line 2 |

## Updatable Quote Items
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| idsOfItemsToDelete |  | array of string  |  |  Identifiers of items to delete |
| itemsToUpdate |  | array of [Updatable Quote Item](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-quotas.md#updatable-quote-item) |  | Items to update |
| itemsToAdd |  | array of [Quote Item](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-quotas.md#quote-item) |  | Items to add |

## Updatable Quote Item
| Field | Required | Type | [Updatable](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-quotas.md#updatable-property) | Restrictions | Description |
|--|--|--|--|--|--|
| itemId |  | string  |  | max 64 |  Item identifier|
| productId |  | string  | * | max 64 |  Product identifier|
| unitPrice |  | money | * |  | Product unit price |
| unitCost |  | money | * |  | Product unit price |
| unitWeight |  | float | * |  | Product weight |
| unitOfMeasure |  | [UnitOfMeasure](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#unit-of-measure) | * |  | Unit of measure. |
| quantity |  | integer | * |  | Product quantity in order line |
| tax |  | money   | * | default(0) | Total line tax |
| discount |  | money   | * | default(0) | Total line discount |
| mpn |  | string | * | max 50 | Manufacturer part number |
| itemName |  | string | * | max 2000 | Item name |

## Quote Item
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| productId | * | string  | max 64 |  Product identifier|
| unitPrice | * | money |  | Product unit price |
| unitCost | * | money |  | Product unit price |
| unitWeight | * | float |  | Product weight |
| unitOfMeasure | * | [UnitOfMeasure](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#unit-of-measure) |  | Unit of measure. |
| quantity | * | integer |  | Product quantity in order line |
| tax |  | money   | default(0) | Total line tax |
| discount |  | money   | default(0) | Total line discount |
| mpn |  | string | max 50 | Manufacturer part number |
| itemName |  | string | max 2000 | Item name |

## Updatable Notes
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| idsOfNotesToDelete |  | array of string  |  |  Identifiers of notes to delete |
| notesToUpdate |  | array of [Updatable Note](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-quotas.md#updatable-note) |  | Notes to update |
| notesToAdd |  | array of [Note](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-quotas.md#note) |  | Notes to add |


## Updatable Note
| Field | Required | Type | [Updatable](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-quotas.md#updatable-property) | Restrictions | Description |
|--|--|--|--|--|--|
| noteId | * | string  |  | max 64 |  Note identifier |
| message |  | string  | * | max 2000 | Note message |
| actionTypeCode |  | [ActionTypeCode](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-quotas.md#action-type-code) | * |  | Code of action type. |

## Note
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| message | * | string  | max 2000 |  Note message |
| actionTypeCode |  | [ActionTypeCode](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-quotas.md#action-type-code) |  | Code of action type. |


## Action Type Code

| Code | Description |
|--|--|
| WalkIn | ??? |
| PhoneCall | Phone call. |
| Email | Email message. |
| Fax | Fax message. |
| General | ???. |
| Order | ???. |
| QuestionToSupport | Question to support. |
| Cancel | ???. |

## Updatable Property
See [example](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-quotas.md#valid-request)

| Property | Required | Description |
|--|--|--|
| newValue | * | New value to update. |
| oldValue |  | Old value to handle concurrent updates. |


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
| 2023 February 28 | 20230228.1 |
### Release Notes
* Update customer quote endpoint added.
-------------------------------

