# Send Order General Email

## Path
/v1/order/{orderId}/email/send-general

## Method

POST

## Headers

[require request context](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/authentication.md#request-context)

## Scope
orders:email-general

## Body
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| emailMessage | * |Complex type [Email Message](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/emails.md#email-message)  |  | Email Message. |

## Valid Request
```
{
    "emailMessage":
    {
        "to":[{"email":"some.address@somedomain.com", "name":"John Doe"}],
        "content":"<p>Hello John!</p><p><b>How are you?</b></p>",
        "subject":"Have a good day!",
        "cc":{"email":"copy.addres@otherdomain.com"},
        "attachments":[{"filename":"some.pdf", "content":"PHA+SGVsbG8gSm9obiE8L3A+PHA+PGI+SG93IGFyZSB5b3U/PC9iPjwvcD4="}]
    }

}
```

## Success Response

HTTP Status Code: 200

Example:
```
{
    "submissionId": "713mm825-3372-4de0-848a-accda64d4a0b"
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
    "traceId": "8412a15b-c2ef-4916-9b09-d336579e94e3",
    "errors": {
        "cc.name": [
            "The length of 'name' must be at least 2 characters. You entered 0 characters."
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

# Get Order Email Templates

## Path
/v1/order/{orderId}/email/templates

## Method

GET

## Headers

[require request context](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/authentication.md#request-context)

## Scope
orders:email-templated

## Response Contracts

### Email Template
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| code | * | string  | | Template code. |
| name | * | string  | | Template name. |
| availableOptions |  | List of [Email Template Available Option](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/order-emails.md#Email-Template-Available-Option)  | | Available options. |

### Email Template Available Option
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| code | * | string  | | Option code. |
| name | * | string  | | Option name. |

## Success Response

HTTP Status Code: 200

Example:
```
{
 "payload": [
    {
        "code": "email_a_friend",
        "name": "!!!! Email a friend",
        "availableOptions": [
            {
                "code": "details",
                "name": "Attach order details"
            },
            {
                "code": "details_with_sugnature",
                "name": "Attach order details with signature"
            }
        ]
    },
    {
        "code": "account_created",
        "name": "!!! Account Created",
        "availableOptions": [
            {
                "code": "details",
                "name": "Attach order details"
            },
            {
                "code": "details_with_sugnature",
                "name": "Attach order details with signature"
            }
        ]
    }
  ]
}
```

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
    "traceId": "d7234748-ba00-4d87-8cf2-246423cc172c"
}
```

# Send Order Templated Email

## Path
/v1/order/{orderId}/email/send-templated

## Method

POST

## Headers

[require request context](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/authentication.md#request-context)

## Scope
orders:email-templated

## Body
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| sendEmailCommand | * |Complex type [Send Email Command](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/order-emails.md#Send-Email-Command)  |  | Send email command. |

### Send Email Command
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| emailTemplateCode | * | string  | Code of [Email Template](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/order-emails.md#Email-Template) | Template code. |
| options |  |Array of [Send Email Template Option](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/order-emails.md#Send-Email-Template-Option)  |  One of AvailableOptions from [Template](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/order-emails.md#email-template)  | Options Array. |

### Send Email Template Option
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| code | * | string  | | Available option code. |

## Valid Request
```
{
    "sendEmailCommand":
    {
        "emailTemplateCode":"account_created",
        "options":[{"code":"details"}]
    }
}
```

## Success Response

HTTP Status Code: 200

Example:
```
{
    "submissionId": "713mm825-3372-4de0-848a-accda64d4a0b"
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
    "traceId": "7c4d9ffe-5b78-4817-9112-8f997c62d415",
    "errors": {
        "sendEmailCommand.options[0]": [
            "'code' should be one of the 'details, details_with_sugnature but not 'details1'."
        ],
        "sendEmailCommand.options[1]": [
            "'code' should be one of the 'details, details_with_sugnature but not 'details2'."
        ],
        "sendEmailCommand.options": [
            "The specified condition was not met for 'options'."
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

# Prepare Order Email by Template

## Path
/v1/order/{orderId}/email/prepare-by-template

## Method

POST

## Headers

[require request context](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/authentication.md#request-context)

## Scope
orders:email-templated

## Body
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| prepareEmailCommand | * |Complex type [Send Email Command](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/order-emails.md#Prepare-Email-Command)  |  | Prepare email command. |

### Prepare Email Command
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| emailTemplateCode | * | string  | Code of [Email Template](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/order-emails.md#Email-Template) | Template code. |
| options |  |Array of [Prepare Email Template Option](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/order-emails.md#Prepare-Email-Template-Option)  |  One of AvailableOptions from [Template](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/order-emails.md#email-template)  | Options Array. |

### Prepare Email Template Option
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| code | * | string  | | Available option code. |

## Valid Request
```
{
    "prepareEmailCommand":
    {
        "emailTemplateCode":"account_created",
        "options":[{"code":"details"}]
    }
}
```

## Success Response

HTTP Status Code: 200

Example:
```
{
    "submissionId": "193mm825-3372-4de0-848a-accda64d4d7c"
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
    "traceId": "7c4d9ffe-5b78-4817-9112-8f997c62d415",
    "errors": {
        "prepareEmailCommand.options[0]": [
            "'code' should be one of the 'details, details_with_sugnature but not 'details1'."
        ],
        "prepareEmailCommand.options[1]": [
            "'code' should be one of the 'details, details_with_sugnature but not 'details2'."
        ],
        "prepareEmailCommand.options": [
            "The specified condition was not met for 'options'."
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

# Send Order Prepared Email by Template

## Path
/v1/order/{orderId}/email/send-prepared-by-template

## Method

POST

## Headers

[require request context](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/authentication.md#request-context)

## Scope
orders:email-templated

## Body

| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| sendEmailCommand | * |Complex type [Send Prepared Email Command](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/order-emails.md#Send-Prepared-Email-Command)  |  | Prepare email command. |

### Send Prepared Email Command

| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| cc |  | [Email Address](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/order-emails.md#Email-Address) |  | Carbon copy email address. |
| bcc |  | [Email Address](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/order-emails.md#Email-Address) |  | Blind carbon copy email address. |
| subject | * | string | max 500 | Message subject. |
| content | * | string |  | Message content. For example html content. |
| EmailTemplateCode |  | string | max 200 | Code of template.  |
| options |  |Array of [Send Prepared Email Template Option](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/order-emails.md#Send-Prepared-Email-Template-Option)  |  One of AvailableOptions from [Template](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/order-emails.md#email-template)  | Options Array. |

### Email Address

| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| email | * | string | | Email address. |
| name |  | string |  | Name. |

### Send Prepared Email Template Option
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| code | * | string  | | Available option code. |

## Valid Request
```
{
	"sendEmailCommand"
	{
		 "to":[{"email":"some.address@somedomain.com", "name":"John Doe"}],
		 "content":"<p>Hello John!</p><p><b>How are you?</b></p>",
		 "subject":"Have a good day!",
		 "cc":{"email":"copy.addres@otherdomain.com"},
		 "options":[{"code":"details"}]
	}
}
```

## Success Response

HTTP Status Code: 200

Example:
```
{
    "submissionId": "313mm825-3372-4de0-848a-accda64d4dec"
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
    "traceId": "7c4d9ffe-5b78-4817-9112-8f997c62d415",
    "errors": {
        "sendEmailCommand.options[0]": [
            "'code' should be one of the 'details, details_with_sugnature but not 'details1'."
        ],
        "sendEmailCommand.options[1]": [
            "'code' should be one of the 'details, details_with_sugnature but not 'details2'."
        ],
        "sendEmailCommand.options": [
            "The specified condition was not met for 'options'."
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

# Operation status

Status operation is the same as [Order operation status](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/create-orders.md#order-operation-status) for create order operation.


