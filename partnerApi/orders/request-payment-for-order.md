# Request Payment for Order

## Path
/v1/order/request-payment

## Method

POST

## Headers

[require request context](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/authentication.md#request-context)

## Scope
orders:request-payment

## Body
Update Customer Quote Request
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| customerOrder | * | [Order for Request Payment](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/request-payment-for-order.md#order-for-request-payment) object |  | Customer order data for request payment serialized as JSON. |


## Valid Request
```
{
	"customerOrder": {
		"orderId": "517231"
	}
}
```

## Success Response

HTTP Status Code: 200

Example:
```
{
    "submissionId": "713dd825-3372-4de0-848a-accda64d4a0b"
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

# Order operation status

Status operation is the same as [Quote operation status](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/create-quotas.md#quote-operation-status) for create quote operation.

# Contracts

## Order for Request Payment

| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| orderId | * | string  | max 64 |  Order identifier|
