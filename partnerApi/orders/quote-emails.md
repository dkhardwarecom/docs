# Send Quote General Email

## Path
/v1/quote/{quoteId}/email/send-general

## Method

POST

## Headers

[require request context](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/authentication.md#request-context)

## Scope
quotas:email-general

## Body
Update Customer Quote Request
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

# Operation status

Status operation is the same as [Quote operation status](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/create-quotas.md#quote-operation-status) for create quote operation.



