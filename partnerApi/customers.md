# Get Customers

## Path
/v1/customer/

## Method

GET

## Scope
customers

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
            "firstName": "Some",
            "lastName": "Person",
            "email": "some.email@some.site",
            "company": "",
            "phone": "4678478",
            "altPhone": null,
            "fax": null,
            "addresses": [
                {
                    "addressId": "187218",
                    "customerId": "874410",
                    "firstName": "Some",
                    "lastName": "Person",
                    "zip": "S9H 4T7",
                    "country": "Canada",
                    "state": "SK",
                    "city": "Swift Current",
                    "address1": "77 Road",
                    "address2": null,
                    "company": null,
                    "phone": "53678538",
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

## Scope
customers

## Success Response

HTTP Status Code: 200

Example:
```
{
    "payload": {
        "customerId": "21762",
        "createdAt": "2015-01-13T22:16:49",
        "updatedAt": "2022-08-02T13:46:00",
        "firstName": "Some",
        "lastName": "Person",
        "email": "some.email@some.site",
        "company": "",
        "phone": "713-254-1161",
        "altPhone": null,
        "fax": null,
        "addresses": [
            {
                "addressId": "187218",
                "customerId": "21762",
                "firstName": "Some",
                "lastName": "Person",
                "zip": "77377",
                "country": "United States",
                "state": "TX",
                "city": "TOMBALL",
                "address1": "456 BIG MOUNTAIN",
                "address2": "",
                "company": "",
                "phone": "513-254-1161",
                "altPhone": "",
                "fax": "",
                "isDefaultBilling": true,
                "isDefaultShipping": false
            },
            {
                "addressId": "187218",
                "customerId": "21762",
                "firstName": "Some",
                "lastName": "Person",
                "zip": "78247",
                "country": "United States",
                "state": "TX",
                "city": "SAN ANTONIO",
                "address1": "128 WETMORE RD",
                "address2": "",
                "company": "",
                "phone": "964-254-1161",
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

# Create Customer

## Path
/v1/customer/create

## Method

POST

## Scope
customers:create

## Body

[Customer](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/customers.md#customer) contract serialized as json **include** addresses.

## Valid Request
```
{
	"firstName": "Some",
	"lastName": "Person",
	"email": "some.email@some.site",
	"company": "",
	"phone": "14562356",
	"altPhone": null,
	"fax": null,
	"addresses": [
		{
			"firstName": "Some",
			"lastName": "Person",
			"zip": "80911",
			"country": "United States",
			"state": "CO",
			"city": "Colorado Springs",
			"address1": "55 Some St",
			"address2": null,
			"company": null,
			"phone": "56235776",
			"altPhone": null,
			"fax": null,
			"isDefaultBilling": true,
			"isDefaultShipping": true
		}
	]
}
```

## Success Response

HTTP Status Code: 200

Example:
```
{
    "submissionId": "77921d3a-7838-40bf-a2d2-e30424d15520"
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
    "traceId": "d5c99cbf-054d-4be1-8f09-c8b198926765",
    "errors": {
        "CustomerId": [
            "'Customer Id' must be empty."
        ],
        "Email": [
            "'Email' must not be empty."
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

# Update Customer

## Path
/v1/customer/update

## Method

POST

## Scope
customers:update

## Body

[Customer](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/customers.md#customer) contract serialized as json **except** addresses.

## Valid Request
```
{
"customerId":"463118",
"firstName": "Some",
"lastName": "Big Person",
"company": "Horns and hooves",
"phone": "14562356",
"altPhone": null,
"fax": "24562456"
}
```

## Success Response

HTTP Status Code: 200

Example:
```
{
    "submissionId": "ddf7db40-5d43-45f0-a260-8015320ed828"
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
    "traceId": "40bd4d7d-195b-4194-898b-727e4f7357bf",
    "errors": {
        "CustomerId": [
            "'Customer Id' must not be empty."
        ],
        "Email": [
            "'Email' must be empty."
        ]
    }
}
```

Example for 500:
```
{
    "status": 500,
    "title": "System error.",
    "traceId": "3a6a590a-1263-4fb0-a330-82e9e62c13c9"
}
```

# Customer operation status

## Path
/v1/customer/status

## Method

POST

## Scope
customers:status

## Body

SubmissionId serialized as json.

| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| SubmissionId | * | string | max 64 | Identifier of operation received at create or update response. |

## Valid Request
```
{
    "submissionId": "77921d3a-7838-40bf-a2d2-e30424d15520"
}
```

## Success Response

HTTP Status Code: 200

Example:
```
{
    "customerId": 463118,
    "status": "Succeeded",
    "errors": null
}
```

Example with errors messages:
```
{
    "customerId": null,
    "status": "Failed",
    "errors": [
        "Property Email failed validation. Error: 'Email' must not be empty."
    ]
}
```
### Statuses

| Status | Description |
|--|--|
| Accepted | Submission accepted, but processing has not started yet. |
| Processing | Processing started. |
| Succeeded | Processed succeeded. | 
| Failed | Processed failed. | 

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
    "traceId": "3a6a590a-1263-4fb0-a330-82e9e62c13c9"
}
```



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
| customerType |  | string value if dictionary [Type of Customer](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/customers.md#type-of-customer) | max 20 | Type of customer |
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

## Type of Customer

| Value | Description |
|--|--|
| business | Business |
| government | Government |
| military | Military |

# Events

## Customer Changed

### Id
customer:changed

### Payload
| Field | Type | Description |
|--|--|--|
| customerIds | Array of string | Identifiers of changed customers.  |
| date |  date and time | UTC date of changes. |

Example:
```
{
	"event": "customer:changed",
	"secret": "40158583e9bd9d122014907b57a60c12",
	"payload": {
		"customerIds": [
			"6235",
			"11345",
			"8737"
		],
		"date":"2022-10-20T11:15:45Z"
	}
}
```

# Releases
-------------------------------
| Date | Version |
|--|--|
| 2022 September 12 | 20220912.1 |
### Release Notes
* Data read endpoints added.
-------------------------------
| Date | Version |
|--|--|
| 2022 September 21 | 20220921.3 |
### Release Notes
* Customer create and update endpoints added.
* Customer operations status endpoint added.
-------------------------------
| Date | Version |
|--|--|
| 2023 January 30 | 20230130.2 |
### Release Notes
* Add Type of Customer field  to customer enpoints.
-------------------------------
