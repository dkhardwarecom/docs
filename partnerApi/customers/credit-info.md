# Get Customer Credit Info

## Path
/v1/customer/{customerId}/credit-info

## Method

GET

## Scope
customers

## Success Response

HTTP Status Code: 200

Example:
```
{
    "payload": {
        "customerId": "9950",
        "creditApproved": true,
        "creditHold": true,
        "creditLimit": 5000.0,
        "balance": 0.01,
        "creditAvailable": null
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
| creditApproved | * | bool |  | Credit is approved flag. In case of credit is approved it is 'true', otherwise 'false'. |
| creditHold |  | bool |  | Credit holded flag. In case of holded it is 'true', otherwise 'false'. |
| creditLimit |  | money  |  | Limit of the ctedit. |
| balance |  | money |  | Customer balance. |
| creditAvailable |  | money |  | Amount of available credit. ( = creditLimit - balance) |

# Releases
-------------------------------
| Date | Version |
|--|--|
| 2023 September 27 | 20230927.1 |
### Release Notes
* Customer credit info endpoint added.
-------------------------------
