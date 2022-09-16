# Get Vendors

## Path
/v1/vendor/

## Method

GET

## Query Parameters
| Name | Required | Type | Restrictions | Description |
|--|--|--|--|--|

## Success Response

HTTP Status Code: 200

Example:
```
{
    "payload": [
        {
             ...
```

## Error Response


| HTTP status code | Message |
|--|--|
| 400 |  |
| 500 |  |
|  |  |


# Get Vendor by Id

## Path
/v1/vendor/{vendorId}

## Method

GET

## Success Response

HTTP Status Code: 200

Example:
```
{
    "payload": {
       
        
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
## Vendor
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
|  vendorId | * | string | max 64 | Vendor's identifier |
| name |  | string | max 300 | Vendor's name |
| code|  | string | max 32 |  Vendor's code (Business key) |
| company |  | string | max 250 | Full Company name |
| phone |  | string | max 50 | Phone number |
| altPhone | | string | max 50 | Alternative phone number |
| fax |  | string |  max 50 | Fax|
| email | * | string | max 100 | Email address|
| notes |  | string |   | Notes about vendor |
| addresses |  |[Address](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/customers.md#address)[] |  | Vendor's addresses|

# Releases
-------------------------------
| Date | Version |
|--|--|
| 2022 September 12 | 20220912.1 |
### Release Notes
* Data read endpoints added.
-------------------------------

