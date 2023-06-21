# Get Customer Addresses

## Path
/v1/customer/{customerId}/address

## Method

GET

## Scope
customers

## Success Response

HTTP Status Code: 200

Example:
```
 [
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
 ```

## Error Response

| HTTP status code | Message |
|--|--|
| 400 |  |
| 500 |  |
| 404 |  |

# Create Customer Address

## Path
/v1/customer/{customerId}/address/create

## Method

POST

## Headers

[require request context](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/authentication.md#request-context)

## Scope
customers:update

## Body

[Customer Address](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/customers.md#address) contract serialized as json.

## Valid Request
```
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

# Update Customer Address

## Path
/v1/customer/{customerId}/address/update

## Method

POST

## Headers

[require request context](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/authentication.md#request-context)

## Scope
customers:update

## Body

[Customer Address](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/customers.md#address) contract serialized as json include address id.

## Valid Request
```
{
"customerId":"463118",
"addressId":"67234",
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

# Delete Customer Address

## Path
/v1/customer/{customerId}/address/delete

## Method

POST

## Headers

[require request context](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/authentication.md#request-context)

## Scope
customers:update

## Body

| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| AddressId | * | string | max 64 | Identifier of customer address to delete. |


## Valid Request
```
{
  "addressId":"67234"
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
        "addressId": [
            "'Address Id' must not be empty."
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



# Releases
-------------------------------
| Date | Version |
|--|--|
| 2022 September 21 | 20220921.3 |
### Release Notes
* Customer addresses create, update and delete endpoints added.
-------------------------------
