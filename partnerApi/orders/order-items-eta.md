# Get Order Items Estimated Time of Arrival

## Path
/v1/order/{orderId}/items-eta

## Method

GET

## Scope
orders

## Response Contracts

### Payload
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| orderEntityId | * | string | | Id of order entity. In case of customer order it is 'orderId'. |
| itemsEta |  | Array of [Item ETA](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/order-items-eta.md#item-eta)  | | Estimated time of arrival for order items. |

### Item ETA
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| itemId | * | string | | Id of order item. |
| quantity | * | integer  | | Product quantity in order line. |
| estimatedTimeOfArrival | * | date  | | Estimated time (date) of arrival. |

## Success Response

HTTP Status Code: 200

Example:
```
{
    "payload": {
        "orderEntityId": "2020928",
        "itemsEta": [
            {
                "itemId": "4128482",
                "quantity": 38,
                "estimatedTimeOfArrival": "2024-08-02T00:00:00"
            },
            {
                "itemId": "4128482",
                "quantity": 90,
                "estimatedTimeOfArrival": "2024-07-29T00:00:00"
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
