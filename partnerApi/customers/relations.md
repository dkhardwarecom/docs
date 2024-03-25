# Get Customer Relations

## Path
/v1/customer/{customerId}/relations

## Method

GET

## Scope
customers:relations

## Success Response

HTTP Status Code: 200

Example:
```
{
    "payload": {
        "customerId": "459202",
        "orderEntities": {
            "quotas": null,
            "orders": [
                {
                    "orderId": "625595",
					"replacementForOrderId": null,
                    "replacementOrderIds": [],
                    "returnIds": [],
                    "vendorOrderIds": [],
                    "shoppingCartId": "0b38d1b8-5fb3-40e9-bbd0-343d704640d5",
                    "createdAt": "2020-06-09T13:17:38",
                    "total": 432.89,
                    "currency": "USD",
                    "currentStatus": {
                        "id": "7",
                        "name": "New Orders"
                    },
                    "status": "New Orders",
                    ...
                    "payments": null,
                    "shipments": null
                },
                {
                    "orderId": "625606",
                    "parentQuoteId": null,
					"replacementForOrderId": null,
                    "replacementOrderIds": [],
                    "returnIds": [],
                    "vendorOrderIds": [
                        625607
                    ],
                    "shoppingCartId": "81d42d00-f8c6-4589-906e-8fd4d03f1d6c",
                    "createdAt": "2020-06-11T11:38:00",
                    "total": 12.01,
                    "currency": "USD",
                    "currentStatus": {
                        "id": "11",
                        "name": "Shipped Orders - PAID"
                    },
                    "status": "Shipped Orders - PAID",
                    ...
                    "payments": [
                        {
                            "paymentId": "536832",
                            "originalPaymentId": null,
                            "amount": 12.01,
                            "user": {
                                "id": "105",
                                "name": "Alena testST"
                            },
                            "paymentDate": "2020-06-11T15:38:43",
                            "paymentMethod": {
                                "id": "3",
                                "code": "google-checkout",
                                "name": "Google Checkout"
                            },
                            "paymentType": "Charge"
                        }
                    ],
                    "shipments": null
                }
                
            ],
            "returns": [
                {
                    "returnId": "625600",
                    "parentOrderId": 624353,
                    "shoppingCartId": "e691f847-f37b-4573-b39b-fec5879b5de5",
                    "createdAt": "2020-06-11T07:54:03",
                    "total": null,
                    "currency": "USD",
                    "currentStatus": {
                        "id": "5",
                        "name": "RMA Received"
                    },
                    "status": "RMA Received",
                    "payments": null,
                    "shipments": null
                },
                {
                    "returnId": "625601",
                    "parentOrderId": 624353,
                    "shoppingCartId": "0d2f18de-5c28-4a1f-a26e-3fa9bef502f1",
                    "createdAt": "2020-06-11T07:57:44",
                    "total": null,
                    "currency": "USD",
                    "currentStatus": {
                        "id": "64",
                        "name": "RMA Completed and Invoiced"
                    },
                    "status": "RMA Completed and Invoiced",
                    "payments": null,
                    "shipments": null
                }
            ],
            "vendorQuotas": null,
            "vendorOrders": null,
            "vendorReturns": null
        }
    }
}
 ```

## Error Response

| HTTP status code | Message |
|--|--|
| 400 |  |
| 500 |  |
| 404 |  |

# Contracts

## Payload
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| customerId | * | string | max 64 | Customer identifier |
| orderEntities | * | [Order Entities]() |  | Customer order entities relations. |

## Order Entities
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| quotas |  | Array of [Quote](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#quote) |  | Customer related quotas. |
| orders |  | Array of [Order](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#order) |  | Customer related orders. |
| returns |  | Array of [Return](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#return-rma) |  | Customer related RMAs. |
| vendorQuotas |  | Array of [Vendor Quote](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#vendor-quote) |  | Customer related vendor quotas. |
| vendorOrders |  | Array of [Vendor Order](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#vendor-order) |  | Customer related vendor orders. |
| vendorReturns |  | Array of [Vendor Return](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders.md#vendor-return-rma) |  | Customer related vendor RMAs. |

# Releases
-------------------------------
| Date | Version |
|--|--|
| 2024 March ?? | ??? |
### Release Notes
* Customer relations endpoint added.
-------------------------------
