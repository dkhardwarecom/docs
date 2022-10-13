# Get Shipping Rates

## Path

/v1/shipping/rates

## Method

POST

## Scope
shipping

## Query Parameters

### Shipping Rates Request
| Name | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| OrderItems| * | Array of [Order Item](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/shipping.md#order-item) |  | Order items with id and quantity |
| DeliveryAddress | * |Complex type [Country and State Delivery Address](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/shipping.md#country-and-state-delivery-address)  |  | Address to delivery |
| OrderSubTotal |  | Money | | Amount of order subtotal |

### Country and State Delivery Address
| Name | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| Country | * | string(2)|  | Country code. For example: "US" for USA, "IN" for India, "RU" for Russian Federation. |
| StateCode |  | string(?)  |  | Code of region. |

### Order Item
| Name | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| ProductId | * | long integer |  | Id of product. |
| Quantity | * | integer  |  | Quantity to order. |

## Body

[Customer](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/customers.md#customer) contract serialized as json **include** addresses.

## Valid Request
```
{
    "OrderItems":[
         {"productId":40384, "Quantity":1}
        ,{"productId":31399, "Quantity":1}
        ],
    "OrderSubTotal":95.39,
    "DeliveryAddress": {
        "Country":"US"
        }
}
```

## Success Response

HTTP Status Code: 200

Example:
```
{
    "payload": {
        "shippingRates": [
            {
                "id": 1,
                "default": true,
                "title": "Standard Ground",
                "shipping": {
                    "total": 110.37,
                    "shippingCost": 14.98,
                    "handlingFee": 0.0,
                    "userSpecific": null
                },
                "delivery": {
                    "businessDays": {
                        "from": 2,
                        "to": 5
                    },
                    "dateUtc": {
                        "from": "2022-10-17T11:37:00Z",
                        "to": "2022-10-20T11:37:00Z"
                    },
                    "cutOffUtc": "2022-10-14T04:00:00Z"
                }
            },
            {
                "id": 2,
                "default": false,
                "title": "2 Business Days",
                "shipping": {
                    "total": 189.26,
                    "shippingCost": 88.88,
                    "handlingFee": 4.99,
                    "userSpecific": null
                },
                "delivery": {
                    "businessDays": {
                        "from": 0,
                        "to": 2
                    },
                    "dateUtc": {
                        "from": null,
                        "to": "2022-10-17T11:37:00Z"
                    },
                    "cutOffUtc": "2022-10-13T17:00:00Z"
                }
            },
            {
                "id": 4,
                "default": false,
                "title": "1 Business Day",
                "shipping": {
                    "total": 232.13,
                    "shippingCost": 131.75,
                    "handlingFee": 4.99,
                    "userSpecific": null
                },
                "delivery": {
                    "businessDays": {
                        "from": 0,
                        "to": 1
                    },
                    "dateUtc": {
                        "from": null,
                        "to": "2022-10-14T11:37:00Z"
                    },
                    "cutOffUtc": "2022-10-13T17:00:00Z"
                }
            }
        ]
    }
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
    "traceId": "1e8a6479-253b-42a7-a6a4-f96e716197ee",
    "errors": {
        "DeliveryAddress.Country": [
            "'Delivery Address Country' must not be empty."
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

# Contracts

## Shipping Rate

| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| id | * | string | max 64 | Shipping method identifier |
| default | * | boolean |  | Flag for default method |
| title | * | string | max 250 | Shipping method title.  |
| shipping | * | Complex type [Shipping info](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/shipping.md#shipping-info) |  | Information about shipping |
| delivery | * | Complex type [Delivery info](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/shipping.md#delivery-info) |  | Information about delivery |

## Shipping Info

| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| total | * | money | | Total in USD |
| shippingCost | * | money |  | Cost of shipping in USD |
| handlingFee | * | money |  | Handling fee in USD  |

## Delivery Info

| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| businessDays.from |  | integer | | Minimum days for delivery |
| businessDays.to |  | integer | | Maximum days for delivery |
| dateUtc.from | * | date and time | UTC | Minimum date and time for delivery |
| dateUtc.to | * | date and time | UTC | Maximum date and time for delivery |
| cutOffUtc | * | date and time | UTC | Shipping rate expiration |



