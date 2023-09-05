# Get Vendors

## Path
/v1/vendor/

## Method

GET

## Scope
vendors

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
            "vendorId": "46",
            "name": "A. Geo. Diack Inc",
            "code": null,
            "company": null,
            "phone": null,
            "altPhone": null,
            "fax": null,
            "email": null,
            "notes": null,
            "addresses": null,
            "warehouses": [
                {
                    "id": "202",
                    "abbr": "AGDK",
                    "isMain": true,
                    "inbound": false,
                    "priority": 99,
                    "locationAddress": {
                        "country": null,
                        "city": "City of Industry",
                        "state": "CA",
                        "zip": "91745-2408",
                        "address": "1250 S Johnson Dr",
                        "address2": null,
                        "phone": "467812491"
                    }
                }
            ]
        },
        {
            "vendorId": "47",
            "name": "Mutual Industries",
            "code": null,
            "company": null,
            "phone": null,
            "altPhone": null,
            "fax": null,
            "email": "msbei@mutualindustries.com",
            "notes": null,
            "addresses": null,
            "warehouses": [
                {
                    "id": "194",
                    "abbr": "MutualInd",
                    "isMain": true,
                    "inbound": false,
                    "priority": 99,
                    "locationAddress": {
                        "country": null,
                        "city": "Philadelphia",
                        "state": "PA",
                        "zip": "19120",
                        "address": "707 W. Grange St",
                        "address2": null,
                        "phone": "800-000-0888"
                    }
                }
            ]
        }
    ]
}
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

## Scope
vendors

## Success Response

HTTP Status Code: 200

Example:
```
{
    "payload": {
        "vendorId": "35",
        "name": "Top Notch",
        "code": "TopNotch",
        "company": "Top Notch Distributors, Inc.",
        "phone": "",
        "altPhone": "",
        "fax": "",
        "email": null,
        "notes": null,
        "addresses": [
            {
                "addressId": "996508",
                "firstName": "Rem",
                "lastName": "Rem Zam",
                "zip": "33142",
                "country": "United States",
                "state": "CO",
                "city": "Miami",
                "address1": "NW 25th St suite 400",
                "address2": "",
                "company": "Top Notch Distributors, Inc.",
                "phone": "888890000",
                "altPhone": "",
                "fax": "",
                "isDefaultBilling": true,
                "isDefaultShipping": true
            }
        ],
        "warehouses": [
            {
                "id": "125",
                "abbr": "MO",
                "isMain": true,
                "inbound": false,
                "priority": 1,
                "locationAddress": {
                    "country": null,
                    "city": "",
                    "state": "MO",
                    "zip": "63045",
                    "address": "",
                    "address2": "",
                    "phone": ""
                }
            },
            {
                "id": "126",
                "abbr": "PA",
                "isMain": false,
                "inbound": false,
                "priority": 99,
                "locationAddress": {
                    "country": null,
                    "city": "Honesdale",
                    "state": "PA",
                    "zip": "18431",
                    "address": "80 Fourth Street",
                    "address2": null,
                    "phone": " "
                }
            },
            {
                "id": "127",
                "abbr": "NV",
                "isMain": false,
                "inbound": false,
                "priority": 99,
                "locationAddress": {
                    "country": null,
                    "city": "Carson City",
                    "state": "NV",
                    "zip": "89706",
                    "address": "3151 Goni Road",
                    "address2": null,
                    "phone": ""
                }
            },
            {
                "id": "128",
                "abbr": "MA",
                "isMain": false,
                "inbound": false,
                "priority": 99,
                "locationAddress": {
                    "country": null,
                    "city": "Hingham",
                    "state": "MA",
                    "zip": "02043",
                    "address": "72 Sharp St",
                    "address2": null,
                    "phone": ""
                }
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
| warehouses |  |[Warehouse](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/vendors.md#warehouse)[] |  | Vendor's warehouses|

## Warehouse
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| id | * | string | max 64 | Warehouse's identifier |
| abbr | * | string | max 30 | Vendor's abbreviation |
| isMain | * | bool | | Main warehouse flag |
| inbound | * | bool | | Inbound warehouse flag |
| priority | * | integer | positive integer | Warehouse priority |
| locationAddress |  | [Warehouse Location Address](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/vendors.md#warehouse-location-address)[]  | | Warehouse location address |

## Warehouse Location Address
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| country |  | string | max 150 | Country name |
| city |  | string | max 255 | City |
| state |  | string | max 50 | State or region |
| zip |  | string | max 50 | Zip/Postal code |
| phone |  | string | max 50 | Phone number |
| address1 |  | string  | max 255 | Address line 1 |
| address2 |  | string  | max 255 | Address line 2 |

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
| 2023 September 5 | 20230905.2 |
### Release Notes
* Vendor warehouses data added.
-------------------------------

