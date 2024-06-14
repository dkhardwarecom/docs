# Change Quote Status

## Path
/v1/order/change-status

## Method

POST

## Headers

[require request context](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/authentication.md#request-context)

## Scope
orders:change-status

## Body
Change Customer Order Status Request
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| customerOrder | * | [Order for Change Status](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/order-change-status.md#Order-for-Change-Status) object |  | Customer order data for change status serialized as JSON. |



### Order for Change Status

| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| orderId | * | string  | max 64 |  Order identifier|
| statusId | * | [Updatable Property](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-orders.md#updatable-property) |  | Status id value. |

## Valid Request
```
{
	"customerOrder": {
		"orderId": "629268",
        "statusId": { "oldValue":"7","newValue":"19" }
	}
}
```

## Success Response

HTTP Status Code: 200

Example:
```
{
    "submissionId": "713mm825-3372-4de0-848a-accda64d4a0b"
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
        "orderId": [
            "'orderId' should be a valid id."
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
