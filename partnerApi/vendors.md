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
