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
| SubmissionId | * | string | max 64 | Identifier of operation received at specfic response. |

## Valid Request
```
{
    "submissionId": "17e6a31b-f48a-4b9f-ab36-fdcda6dda737"
}
```

## Success Response

HTTP Status Code: 200

Example:
```
{
    "orderId": "538368",
    "status": "Succeeded",
    "errors": null
}
```

Example with errors messages:
```
{
    "orderId": 538368,
    "status": "Failed",
    "errors": [
        "Order payment could not be requested for order at status 'Cancelled'"
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

## Order for Request Payment

| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| orderId | * | string  | max 64 |  Order identifier|
