# Payment Method

## Path
v1/dictionary/payment-method

## Method

GET

## Scope
dictionaries

## Dictionary Value
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| code | * | string | max 50 | Payment method code. |
| name |   | string | max 50 | Payment method name. |

## Success Response

HTTP Status Code: 200

Example:
```
[
    {
        "code": "credit-card",
        "name": "Credit Card"
    },
    {
        "code": "paypal",
        "name": "Paypal"
    },
    {
        "code": "net-30",
        "name": "Net 30"
    },
    {
        "code": "net-15",
        "name": "Net 15"
    },
    {
        "code": "net-7",
        "name": "Net 7"
      
             ...
```

# Shipping Method

## Path
v1/dictionary/shipping-method

## Method

GET

## Scope
dictionaries

## Dictionary Value
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| name |   | string | max 100 | Shipping method name. |

## Success Response

HTTP Status Code: 200

Example:
```
[
    {
        "name": "Standard Ground"
    },
    {
        "name": "2 Business Days"
    },
    {
        "name": "1 Business Day"
    },

  ...
]
```

# Customer Type

## Path
v1/dictionary/customer-type

## Method

GET

## Scope
dictionaries

## Dictionary Value
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| code | * | string | max 50 | Customer type code. |
| name |   | string | max 50 | Customer type name. |

## Success Response

HTTP Status Code: 200

Example:
```
[
    {
        "code": "business",
        "name": "Business"
    },
    {
        "code": "government",
        "name": "Government"
    },
    {
        "code": "military",
        "name": "Military"
    }
]
```


# Releases
-------------------------------
| Date | Version |
|--|--|
| 2023 September 22 | 20230922.1 |
### Release Notes
* Dictionaries endpoints added.
-------------------------------
