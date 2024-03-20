
# Get Order Email By Note Id

## Path
/v1/order/{orderId}/email/by-note/{noteId}

## Method

GET

## Headers

[require request context](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/authentication.md#request-context)

## Scope
orders:email-by-note-id

## Response Contracts
Common [Email Message](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/emails.md#email-message) fields and extra fields


### Note Email Message Extra Fields
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| from |  | [Email Address](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/emails.md#email-address)  | | From address. |
| delivered | * | bool  | | Email has delivered if it is 'true' and vice versa. |

## Success Response

HTTP Status Code: 200

Example:
```
{
    "payload": {
        "from": {
            "email": "pearld@dkhardware.com",
            "name": null
        },
        "delivered": true,
        "to": [
            {
                "email": "KNICKERBOCKER308@OUTLOOK.COM",
                "name": null
            }
        ],
        "cc": {
            "email": "sales@dkhardware.com",
            "name": null
        },
        "bcc": null,
        "subject": "Your DK Hardware Supply  Order request DKH-1784691",
        "content": "<table style=\" width:100%; background-color:#ffffff; border-spacing: 0px;\"> ...",
        "attachments": [
            {
                "content": "JVBERi0xLjQKJaqrrK0KMSAwIG9iago8PAovQ3JlYXRvciAoQXBhY2hlIEZPUCBWZXJzaW9uIDI ...",
                "filename": "Invoice.0ecbc0404ab74505b7ac379ca4639c95.pdf"
            }
        ],
        "templateName": "Order Invoice"
    }
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
