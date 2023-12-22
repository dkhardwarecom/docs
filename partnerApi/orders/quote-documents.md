# Upload Document

## Path

/v1/quote/{quoteId}/document/upload

## Method

POST

## Headers

[require request context](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/authentication.md#request-context)

| Name | Required |  Restrictions | Description |
|--|--|--|--|
| Document-Name | * | max512  | Document name. For example: 'application.pdf' or 'test PDF doc' |
| Content-Disposition | * |   | Used to transfer name of file. For example: ```attachment; filename="test.pdf"``` |

## Scope
quotas:documents

## Body

Binary file contetnt.

## Success Response

HTTP Status Code: 200

Example:
```
{
    "payload": {
        "orderId": 659197,
        "documentId": 98455,
        "documentName": "test PDF doc",
        "fileName": "test.pdf",
        "mimeType": "application/pdf",
        "fileSize": 58116,
        "createdAt": "2023-12-22T08:36:56.9728464Z"
    }
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
    "title": "Document name too long. Should be less than 512.",
    "traceId": "879256b1-a771-4cd7-879b-e454b84836f8"
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
