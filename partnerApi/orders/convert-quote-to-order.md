# Convert Quote to Order

## Path
/v1/quote/convert-to-order

## Method

POST

## Headers

[require request context](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/authentication.md#request-context)

## Scope
quotas:convert-to-order

## Body
Update Customer Quote Request
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| customerQuote | * | [Quote to Convert](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/convert-quote-to-order.md#quote-to-convert) object |  | Customer quote data for convert serialized as JSON. |


## Valid Request
```
{
	"customerQuote": {
		"quoteId": "329277"
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
        "quoteId": [
            "'quoteId' should be a valid id."
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

### Response for operation 'convert-to-order'
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| orderId |  | string  | max 64 |  Identifier of order converted from quote. |
| status  | * | [Enum of Status](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/create-quotas.md#statuses) | enum | Operation status. |
| errors  |   | array of string  | |  Array of error messages. |

## Success Response

HTTP Status Code: 200

Example:
```
{
    "orderId": "778369",
    "status": "Succeeded",
    "errors": null
}
```

# Contracts

## Quote to Convert

| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| quoteId | * | string  | max 64 |  Quote identifier|
