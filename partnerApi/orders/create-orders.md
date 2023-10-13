
# Create Order

## Path
/v1/order/create

## Method

POST

## Headers

[require request context](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/authentication.md#request-context)

## Scope
orders:create

## Body
Create Customer Order Request
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| customerOrder | * | [Order](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/create-orders.md#order) object |  | Customer order object serialized as JSON. |
| referenceId |  | string | max 64 | Id of order in external system. |

## Valid Request
```
{
	"referenceId": "87",
	"customerOrder": {
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

# Order operation status

## Path
/v1/order/status

## Method

POST

## Headers

[require request context](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/authentication.md#request-context)


## Scope
orders:status

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
| orderId | Identifier of order. |
| status | [Status of operation](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/create-orders.md#statuses). |
| errors | Array of errors strings. |
| payload | Order data. The same as [get order response](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#get-orders). |
| referenceId |  Id of order in external system. |

## Success Response

HTTP Status Code: 200

Example:
```
{
    "orderId": "643543",
    "status": "Succeeded",
    "errors": null,
    "referenceId": "329523",
    "payload": {
        "orderId": "643543",
        "orderIds": [],
        "createdAt": "2023-08-09T11:53:30",
        "total": 43.0,
        "currency": "USD",
        "status": "New Web Orders Inquiry",
        "statusId": "22",
        "type": "Orders",
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
    "orderId": null,
    "status": "Failed",
    "errors": [
        "Same reference ID already was used for another order or in another request"
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

## Order

| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| customerId | * | string | max 64  | Customer's identifier |
| customerNotes | | string | max 8000 | Customer's notes or Cutting instructions |
| shippingPrice | * | money  |  | Shipping price |
| shippingTax | * | money  |  | Shipping tax |
| shippingDiscount | | money  | default(0) | Shipping discount |
| handlingFee | | money  | default(0) | Handling fee|
| total | * | money |  | Order total |
| billing | | fields from [Address](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#address) |  | Billing address |
| shipping | | fields from [Address](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#address) |  | Shipping address |
| items | * | array of [Order Item](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/create-orders.md#order-item) |  | Items for order |
| сomment |  | string | max 1000 | Order operator comment. |
| responseTime |  | [Response Time](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/create-orders.md#response-time) enum | | Expected response time for order. |
| paymentMethodCode | * | string  | code from [Dictionary](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/dictionaries.md#payment-method) | Code of Payment method |
| poNumber |  | string  |  | Purchase Order Number |
| orderDateUtc | * | datetime  | UTC | Date of order at UTC format |
| shippingMethod | * | string  | name from [Dictionary](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/dictionaries.md#shipping-method) | Name of Shipping method |

## Order Item
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
| addons |  | array of [Order Item Addon](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#order-item-addon) |  | Item addons. |


## Response Time

| Enum Value | Description |
|--|--|
| Unknown | Response time is unknown. Use any response time. |
| OneDay | Response time is 1 day. |
| ThreeDays | Response time is 3 days. |
| FiveDays | Response time is 5 days. |


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
* Create customer order endpoint added.
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
* poNumber is not required for create order.
-------------------------------
