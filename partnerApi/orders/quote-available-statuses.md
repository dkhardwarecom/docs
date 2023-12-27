# Get Quote Available Statuses

## Path
/v1/quote/{quoteId}/available-statuses

## Method

GET

## Headers

[require request context](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/authentication.md#request-context)

## Scope
quotas

## Response Contracts

### Email Template
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| currentStatus | * | [Current Status](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#order-status) | | Current Status. |
| nextAvailableStatuses |  | Array of [Available Status](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#order-status)  | | Next available statuses. |

## Success Response

HTTP Status Code: 200

Example:
```
{
    "payload": {
        "currentStatus": {
            "id": "22",
            "name": "New Web Quotes Inquiry"
        },
        "nextAvailableStatuses": [
            {
                "id": "3",
                "name": "Cancelled Quotes"
            },
            {
                "id": "39",
                "name": "Converted to order"
            },
            {
                "id": "48",
                "name": "Quotes sent to Customer - Final"
            }
        ]
    }
}
```

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
    "traceId": "d7234748-ba00-4d87-8cf2-246423cc172c"
}
```
