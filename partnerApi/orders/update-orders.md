
# Update Order

## Path
/v1/order/update

## Method

POST

## Headers

[require request context](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/authentication.md#request-context)

## Scope
orders:update

## Body
Update Customer Order Request
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| customerOrder | * | [Updatable Order](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-orders.md#updatable-order) object |  | Customer order data for update serialized as JSON. |


## Valid Request
```
{
	"customerOrder": {
		"orderId": "629265",
		"orderTotals": {
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
        "orderTotals.handlingFee.NewValue": [
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

# Order operation status

Status operation is the same as [Order operation status](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/create-orders.md#order-operation-status) for create order operation.

# Contracts

## Updatable Order

| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| orderId | * | string  | max 64 |  Order identifier|
| orderTotals |  | fields from [Updatable Order Totals](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-orders.md#updatable-order-totals) |  | Order totals data for update |
| billing |  | fields from [Updatable Order Address](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-orders.md#updatable-order-address) |  | Billing address |
| shipping |  | fields from [Updatable Order Address](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-orders.md#updatable-order-address) |  | Shipping address |
| items |  | fields from [Updatable Order Items](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-orders.md#updatable-order-items) |  | Items for update |
| addons |  | fields from [Updatable Order Items Addons](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-orders.md#updatable-order-items-addons) |  | Items addons for update |
| notes |  | fields from [Updatable Notes](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-orders.md#updatable-notes) |  | Notes for update |

## Updatable Order Totals
All properties are [Updatable](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-orders.md#updatable-property)

| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| shippingPrice |  | money  | greater or equal than zero | Shipping price |
| shippingTax |  | money  | greater or equal than zero | Shipping tax |
| shippingDiscount |  | money  | greater or equal than zero | Shipping discount |
| handlingFee |  | money  | greater or equal than zero | Handling fee |
| paymentMethodCode |  | string  | code from [Dictionary](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/dictionaries.md#payment-method) | Code of payment method |



## Updatable Order Address
All properties are [Updatable](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-orders.md#updatable-property)

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

## Updatable Order Items
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| idsOfItemsToDelete |  | array of string  |  |  Identifiers of items to delete |
| itemsToUpdate |  | array of [Updatable Order Item](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-orders.md#updatable-order-item) |  | Items to update |
| itemsToAdd |  | array of [Order Item](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-orders.md#order-item) |  | Items to add |

## Updatable Order Item
| Field | Required | Type | [Updatable](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-orders.md#updatable-property) | Restrictions | Description |
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
| linePosition |  | integer | * |sequence from 1..1000 unique for each item | Position of item line |
| lineComment |  | string | * | max 2000 | Comment for item line |

## Order Item
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| itemId | * | string  | max 64 |  Item identifier |
| productId | * | string  | max 64 |  Product identifier|
| unitPrice | * | money |  | Product unit price |
| unitCost | * | money |  | Product unit price |
| unitWeight | * | float |  | Product weight |
| unitOfMeasure | * | [UnitOfMeasure](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#unit-of-measure) |  | Unit of measure. |
| quantity | * | integer |  | Product quantity in order line |
| tax | * | money   | default(0) | Total line tax |
| discount | * | money   | default(0) | Total line discount |
| mpn | * | string | max 50 | Manufacturer part number |
| itemName | * | string | max 2000 | Item name |
| linePosition | * | integer | sequence from 1..1000 unique for each item | Position of item line |
| lineComment |  | string | max 2000 | Comment for item line |

## Updatable Notes
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| idsOfNotesToDelete |  | array of string  |  |  Identifiers of notes to delete |
| notesToUpdate |  | array of [Updatable Note](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-orders.md#updatable-note) |  | Notes to update |
| notesToAdd |  | array of [Note](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-orders.md#note) |  | Notes to add |


## Updatable Note
| Field | Required | Type | [Updatable](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-orders.md#updatable-property) | Restrictions | Description |
|--|--|--|--|--|--|
| noteId | * | string  |  | max 64 |  Note identifier |
| message |  | string  | * | max 2000 | Note message |
| actionTypeCode |  | [ActionTypeCode](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#action-type-code) | * |  | Code of action type. |

## Note
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| message | * | string  | max 2000 |  Note message |
| actionTypeCode | * | [ActionTypeCode](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#action-type-code) |  | Code of action type. |

## Updatable Order Items Addons
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| addonsToDelete |  | array of [Addon to Delete](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-orders.md#addon-to-delete)   |  | Addons to delete |
| addonsToUpdate |  | array of [Addon to Update](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-orders.md#addon-to-update) |  | Addons to update |
| addonsToAdd |  | array of [Addon to Add](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-orders.md#addon-to-add) |  | Addons to add |

## Addon to Delete
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| itemId | * | string  | max 64 |  Item identifier |
| code | * | string  | max 64 |  Code of addon|

## Addon to Update
| Field | Required | Type | [Updatable](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-orders.md#updatable-property) | Restrictions | Description |
|--|--|--|--|--|--|
| itemId | * | string | | max 64 |  Item identifier | 
| code | * | string | | max 64 |  Code of addon | 
| price |  | money | * | |  Price of addon | 

## Addon to Add
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| itemId | * | string  | max 64 |  Item identifier |
| code | * | string  | max 64 |  Code of addon |
| price |  | money  |  |  Price of addon |

## Updatable Property
See [example](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-orders.md#valid-request)

| Property | Required | Description |
|--|--|--|
| newValue | * | New value to update. |
| oldValue |  | Old value to handle concurrent updates. |


# Events

## Order Changed

### Id
customer-order:changed

### Payload
| Field | Type | Description |
|--|--|--|
| orderIds | Array of string | Identifiers of changed orders.  |
| date |  date and time | UTC date of changes. |

Example:
```
{
	"event": "customer-order:changed",
	"secret": "78f1a65ff4cc4d8ab6b855cd3c15ff79",
	"payload": {
		"orderIds": [
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
| 2023 September 22 | 20230922.1 |
### Release Notes
* Update customer order endpoint added.
-------------------------------
