# Send General Email

## Path

/v1/email/send

## Method

POST

## Scope
emails:send

## Query Parameters

### Send General Email Request
| Name | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| emailMessage | * |Complex type [Email Message](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/emails.md#email-message)  |  | Email Message. |

## Body

[Send General Email Request](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/emails.md#Send-General-Email-Request) contract serialized as JSON.

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

# Send General Email operation status

## Path

/v1/email/status

## Method

POST

## Scope
emails:status

Status operation is the same as other operations staus. For example [Quote operation status](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/create-quotas.md#quote-operation-status).

# Contracts

## Email Message

| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| to | * | Array of [Email Address](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/emails.md#Email-Address) |  | Collection of email addresses. |
| cc |  | [Email Address](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/emails.md#Email-Address) |  | Carbon copy email address. |
| bcc |  | [Email Address](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/emails.md#Email-Address) |  | Blind carbon copy email address. |
| subject | * | string | max 500 | Message subject. |
| content | * | string |  | Message content. For example html content. |
| attachments |  | Array of [Email Attachment](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/emails.md#Email-Attachment) |  | Collection of email attachments. |
| templateName | * | string | max 200 | Name of template.  |

## Email Address

| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| email | * | string | | Email address. |
| name |  | string |  | Name. |

## Email Attachment

| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| fileName | * | string | max 512 | File name. |
| content | * | string |  | File content encoded as base64. |


