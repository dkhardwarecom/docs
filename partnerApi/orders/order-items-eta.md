# Get Order ETA
## Path
/v1/order/{orderId}/eta

## Method

GET

## Scope
orders

## Response Contracts

### Payload
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| orderId | * | string | | Id of order. |
| etaList |  | List of [Item ETA](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/order-items-eta.md#item-eta)  | | Estimated time of arrival for order items. |

### Item ETA
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| itemId | * | string | | Id of order item. |
| quantity | * | integer  | | Product quantity in order line. |
| eta | * | date  | | Estimated time (date) of arrival. |

## Success Response

HTTP Status Code: 200

Example:
```
{
    "payload": {
        "orderId": "2020928",
        "etaList": [
            {
                "itemId": "4128482",
                "quantity": 38,
                "eta": "2024-08-02"
            },
            {
                "itemId": "4128482",
                "quantity": 90,
                "eta": "2024-07-29"
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
    "traceId": "f7234748-ba00-4d87-8cf2-246423gk172d"
}
```
