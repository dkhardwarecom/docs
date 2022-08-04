# Get Customers

## Path
/v1/customer/

## Method

GET

## Query Parameters
| Name | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| from|  | DateTime| default(null)<br />UTC | From updated (or created) date and time filter value.<br /> Example: /v1/customer?from=2022-03-11T22:15:59Z |
| to|  | DateTime| default(null)<br />UTC | To updated (or created) date and time filter value.<br /> Example: /v1/customer?to=2022-03-13T10:45:11Z |
| newest|  | Boolean| default(true) | If true, return in descending order newest to oldest. |
| limit|  | integer | max 1000, default(100) | Return a number of records with the set limit value. |
| offset |  | integer | default(0) | Return a subset of records starting with the offset value. |
| basedOnCreatedDate|  | Boolean | default(false) | If true, return subset based on created date else updated date |

## Success Response

HTTP Status Code: 200

Example:
```
{
 
}
```

## Error Response


| HTTP status code | Message |
|--|--|
| 400 |  |
| 500 |  |
|  |  |



# Contracts
## Customer

| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| customerId | * | integer |  | Customer's identifier |
| createdAt | * | dateTime |  | Creation date and time in UTC format |
| updatedAt | * | dateTime |  | Updated date and time in UTC format |
| firstName | * | string | max 150 | First name |
| lastName | * | string | max 150 | Last name |
| company |  | string | max 250 | Company name |
| phone |  | string | max 50 | Phone number |
| altPhone | | string | max 50 | Alternative phone number |
| fax |  | string |  max 50 | Fax|
| email | * | string | max 100 | Email address|
| addresses |  |[Address](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/customers.md#address)[] |  | Customer's addresses|


## Address

| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| addressId | * | integer |  | Address identifier |
| customerId | * | integer |  | Customer's identifier |
| firstName | * | string | max 150 | First name |
| lastName | * | string | max 150 | Last name |
| company |  | string | max 250 | Company name |
| phone |  | string | max 50 | Phone number |
| altPhone | | string | max 50 | Alternative phone number |
| fax |  | string |  max 50 | Fax|
| zip | * | string | max 50 | Zip/Postal code |
| country | * | string | max 150 | Country name |
| state | * | string | max 50 | State or region |
| city | * | string | max 255 | City |
| address1 | * | string  | max 255 | Address line 1 |
| address2 |  | string  | max 255 | Address line 2 |
| isDefaultBilling |  | boolean | default(false) | It is default billing address  |
| isDefaultShipping |  | boolean | default(false) | It is default shipping address  |
| createdAt | * | dateTime |  | Creation date and time in UTC format |
| updatedAt | * | dateTime |  | Updated date and time in UTC format |
