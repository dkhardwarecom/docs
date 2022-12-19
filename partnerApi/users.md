# List Users

## Path
/v1/user/

## Method

GET

## Scope
users

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
            "id": "164",
            "name": "John Doe"
        },
        {
            "id": "163",
            "name": "Some Person"
        },
      
             ...
```

## Error Response


| HTTP status code | Message |
|--|--|
| 400 |  |
| 500 |  |
|  |  |


# Contracts
## User
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| id | * | string | max 64 | Users's identifier |
| name |  | string | max 300 | Users's name |

# Releases
-------------------------------
| Date | Version |
|--|--|
| 2022 December 19 | 20221219.1 |
### Release Notes
* User list endpoint added.
-------------------------------
