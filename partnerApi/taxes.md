
# Get Tax for Order

## Path

/v1/tax/for-order

## Method

POST

## Scope
taxes

## Query Parameters

### Tax for Order Request
| Name | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| shippingAddress | * |Complex type [Shipping Address](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/taxes.md#shipping-address)  |  | Address to delivery. |
| email |  | string | valid email address | Customer email to bind exemption rules. |
| callContext| * | Complex type [Call Context](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/taxes.md#call-context) |  | Required data for identify initiator and place of call |
| orderItems| | Array of [Order Item](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/taxes.md#order-item) |  | Order items |
| shippingPrice | | Money | greater than 0 | Price of order shipping. |
| shippingDiscount | | Money | greater than 0 | Discount for order shipping. |
| handlingFee | | Money | greater than 0 | Fee for order handling. |


### Shipping Address
| Name | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| country | * | string | max 2 | Country code. For example: "US" for USA, "IN" for India. |
| state |  | string | Required for country 'US' | Code of region. |
| city |  | string | | City. |
| street |  | string |  | Street. |
| zip |  | string |  | Postal code. |



### Order Item
| Name | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| lineId | * | long | greater than 0, unique for all items | Position (number) of order line. It could be many lines with the same 'ProductId'. |
| productId | * | string | max 64 | Id of product. |
| quantity | * | integer  | greater than 0 | Quantity to order. |
| unitPrice | * | Money  | greater than 0 | Price of one product item for order line. |
| discount |  | Money  | greater than 0 | Discount for one product item for order line. |

For examle:
| LineId | ProductId | Quantity | UnitPrice | Discount |
|--|--|--|--|--|
| 1 | "57632" | 3 | 17.95| |
| 2 | "23311" | 1 | 1216.11| 60.80 |
| 3 | "13476" | 2 | 18.77| |
| 4 | "7632" | 5 | 134.05| |


### Call Context

Used for diagnosic reasons.

| Name | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| userId | * | string | max 128 | Identity of call initiator user account. |
| userName |  | string | max 300 | Name of call initiator user account. |
| initiatedFrom | | string | max 300 | Description of call initiation place. Code or description of Application Form, or an API subsystem alias. For example: 'Order Approving Form', 'Merchant API' |

## Body

[Shipping Rates Request](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/taxes.md#shipping-rates-request) object seralized as JSON.

## Valid Request for Normal status
```
{ "shippingAddress":
    {
        "country":"us",
        "zip":"11222",
        "state":"NY",
        "city":"NewYork",
        "street": "1st av"
    },
    "callContext":{"userId":"54", "userName":"John Doe", "initiatedFrom":"Approve Order Form"},
    "orderItems":[
        {"lineId":"1", "productId":"57632", "quantity":3,  "unitPrice":17.95},
        {"lineId":"2", "productId":"23311", "quantity":1, "unitPrice":1216.11, "discount":60.80 },
        {"lineId":"3", "productId":"13476", "quantity":2,  "unitPrice":18.77},
        {"lineId":"4", "productId":"7632", "quantity":5,  "unitPrice":134.05}
        ],
    "shippingCost":95.39,
    "handlingFee":55.65
}
```

### Success Response

HTTP Status Code: 200

Example:
```
{
    "payload": {
        "tax": 78.90,
        "shippingTax": 2.23,
        "lineItems": [
            {
                "lineId": 1,
                "productId": "57632",
                "tax": 2.15
            },
            {
                "lineId": 2,
                "productId": "23311",
                "tax": 46.21
            },
            {
                "lineId": 3,
                "productId": "13476",
                "tax": 1.50
            },
            {
                "lineId": 4,
                "productId": "7632",
                "tax": 26.81
            }
        ],
        "resultStatus": "Normal"
    }
}
```

## Valid Request for Fallback status
```
{ "shippingAddress":
    {
        "country":"us",
        "zip":"46324",
        "state":"NY",
        "city":"NewYork",
        "street": "1st av"
    },
    "callContext":{"userId":"54", "userName":"John Doe", "initiatedFrom":"Approve Order Form"},
    "orderItems":[
        {"lineId":"1", "productId":"57632", "quantity":3,  "unitPrice":17.95},
        {"lineId":"2", "productId":"23311", "quantity":1, "unitPrice":1216.11, "discount":60.80 },
        {"lineId":"3", "productId":"13476", "quantity":2,  "unitPrice":18.77},
        {"lineId":"4", "productId":"7632", "quantity":5,  "unitPrice":134.05}
        ],
    "shippingCost":95.39,
    "handlingFee":55.65
}
```

### Success Response

HTTP Status Code: 200

Example:
```
{
    "payload": {
        "tax": 161.54,
        "shippingTax": 4.55,
        "lineItems": [
            {
                "lineId": 1,
                "productId": "57632",
                "tax": 4.41
            },
            {
                "lineId": 2,
                "productId": "23311",
                "tax": 94.61
            },
            {
                "lineId": 3,
                "productId": "13476",
                "tax": 3.07
            },
            {
                "lineId": 4,
                "productId": "7632",
                "tax": 54.89
            }
        ],
        "resultStatus": "Fallback",
        "fallbackReasons": [
            "Bad Request - to_zip 46324 is not used within to_state NY"
        ]
    }
}
```

## Valid Request for Exempt status
```
{ "shippingAddress":
    {
        "country":"us",
        "zip":"11222",
        "state":"NY",
        "city":"NewYork",
        "street": "1st av"
    },
    "email":"service@oholeitorah.com",
    "callContext":{"userId":"54", "userName":"John Doe", "initiatedFrom":"Approve Order Form"}
}
```

### Success Response

HTTP Status Code: 200

Example:
```
{
    "payload": {
        "tax": 0,
        "lineItems": [],
        "resultStatus": "Exempt"
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
    "traceId": "6d607a7c-1a0f-4d37-83d8-ddd870707e2b",
    "errors": {
        "OrderItems[2].UnitPrice": [
            "'Unit Price' must not be empty."
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

## Tax for Order
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
|  tax | * | Money | | Tax sum for order. |
|  shippingTax |  | Money | max 100 | Shipping tax sum for order |
|  lineItems |  | Array of [Tax Line Item](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/taxes.md#tax-line-item) | | Detailed tax info by order line items |
|  resultStatus |  | Enum value of [Result Status](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/taxes.md#result-status) | | Status of result. |
|  fallbackReasons |  | Array of string | | Details about fallback reasons in case of Result Status is Fallback. |


## Tax Line Item
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| lineId | * | long | greater than 0, unique for all items | Position (number) of order line of requested [Order Item](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/taxes.md#order-item). |
| productId | * | string | max 64 | Id of product. |
| tax | * | Money  | greater than 0 | Sum of tax for current line item. |

## Result Status
| Value | Description |
|--|--|
|  Normal | Tax result without any anomalies.  |
|  Exempt | Tax exemption was applied.  |
|  Fallback | Result is fallback. See details at [Tax for Order](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/taxes.md#tax-for-order) -> fallbackReasons    |
| Error | Some non critical system error occoured. |

# Releases
-------------------------------
| Date | Version |
|--|--|
| 2022 November 29 | 20221129.4 |
### Release Notes

* Tax for order endpoint added.

-------------------------------
| Date | Version |
|--|--|
| 2022 December 12 | 20221212.1 |
### Release Notes

* Rename 'initiatorAccountId' to 'userId', 'initiatorAccountName' to 'userName'.

-------------------------------

