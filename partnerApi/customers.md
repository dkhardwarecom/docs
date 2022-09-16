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
    "payload": [
        {
            "customerId": "874410",
            "createdAt": "2022-08-05T05:56:44",
            "updatedAt": "2022-08-05T05:56:44",
            "firstName": "Jesse",
            "lastName": "Book",
            "email": "jesse.superbtrucking@gmail.com",
            "company": "",
            "phone": "3068677031",
            "altPhone": null,
            "fax": null,
            "addresses": [
                {
                    "addressId": "187218",
                    "customerId": "874410",
                    "firstName": "Jesse",
                    "lastName": "Book",
                    "zip": "S9H 4T7",
                    "country": "Canada",
                    "state": "SK",
                    "city": "Swift Current",
                    "address1": "405 Northcote DR",
                    "address2": null,
                    "company": null,
                    "phone": "3068677031",
                    "altPhone": null,
                    "fax": null,
                    "isDefaultBilling": false,
                    "isDefaultShipping": true
                },
                ...
```

## Error Response


| HTTP status code | Message |
|--|--|
| 400 |  |
| 500 |  |
|  |  |


# Get Customer by Id

## Path
/v1/customer/{customerId}

## Method

GET

## Success Response

HTTP Status Code: 200

Example:
```
{
    "payload": {
        "customerId": "21762",
        "createdAt": "2015-01-13T22:16:49",
        "updatedAt": "2022-08-02T13:46:00",
        "firstName": "MIKE",
        "lastName": "TIMMONS",
        "email": "timmons.mike@gmail.com",
        "company": "",
        "phone": "713-254-1161",
        "altPhone": null,
        "fax": null,
        "addresses": [
            {
                "addressId": "187218",
                "customerId": "21762",
                "firstName": "MIKE",
                "lastName": "TIMMONS",
                "zip": "77377",
                "country": "United States",
                "state": "TX",
                "city": "TOMBALL",
                "address1": "12030 ECHO CANYON DR",
                "address2": "",
                "company": "",
                "phone": "713-254-1161",
                "altPhone": "",
                "fax": "",
                "isDefaultBilling": true,
                "isDefaultShipping": false
            },
            {
                "addressId": "187218",
                "customerId": "21762",
                "firstName": "MIKE",
                "lastName": "TIMMONS",
                "zip": "78247",
                "country": "United States",
                "state": "TX",
                "city": "SAN ANTONIO",
                "address1": "12891 WETMORE RD",
                "address2": "",
                "company": "",
                "phone": "713-254-1161",
                "altPhone": "",
                "fax": "",
                "isDefaultBilling": false,
                "isDefaultShipping": true
            }
        ]
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
## Customer

| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| customerId | * | string | max 64 | Customer's identifier |
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
| addressId | * | string | max 64 | Address identifier |
| customerId | * | string | max 64 | Customer's identifier |
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

# Releases
-------------------------------
| Date | Version |
|--|--|
| 2022 September 12 | 20220912.1 |
### Release Notes
* Data read endpoints added.
-------------------------------
