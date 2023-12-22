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
        "quoteId": 659197,
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




# Documents List

## Path
/v1/quote/{quoteId}/document/

## Method

GET

## Headers

[require request context](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/authentication.md#request-context)

## Scope
quotas:documents

## Success Response

HTTP Status Code: 200

List of [Document Metadata](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/quote-documents.md#Document-Metadata)

Example:
```
{
    "payload": [
        {
            "quoteId": 623059,
            "documentId": 94012,
            "documentName": "Signed DKH-622643.pdf",
            "fileName": "Signed DKH-622643.pdf",
            "mimeType": "application/pdf",
            "fileSize": 71611,
            "createdAt": "2020-02-06T12:01:12.72"
        },
        {
            "quoteId": 623059,
            "documentId": 94013,
            "documentName": "cc form DKH-622643.pdf",
            "fileName": "cc form DKH-622643.pdf",
            "mimeType": "application/pdf",
            "fileSize": 37530,
            "createdAt": "2020-02-06T12:03:11.1"
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

# Download Document

## Path

/v1/quote/{quoteId}/document/download/{documentId}

## Method

GET

## Headers

[require request context](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/authentication.md#request-context)

| Name | Required |  Restrictions | Description |
|--|--|--|--|
| Accept | * | | Should be ```*/*```.   |


## Scope
quotas:documents

## Success Response

HTTP Status Code: 200

Binary file contetnt.

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
    "title": "Customer quote with id '933864' not found.",
    "traceId": "8f7d0b19-2158-4d50-8431-2bef147d6306"
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

# Delete Document

## Path
/v1/quote/{quoteId}/document/delete

## Method

POST

## Headers

[require request context](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/authentication.md#request-context)

## Scope
quotas:documents

## Body

| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| DocumentId | * | string | max 64 | Identifier of document. |


## Valid Request
```
{
  "documentId":"94013"
}
```

## Success Response

HTTP Status Code: 200

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
    "title": "DocumentId is empty.",
    "traceId": "59cb18b3-fced-4385-b19c-9b4e3c071eeb"
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

# Contracts

## Document Metadata

| Field | Type | Description |
|--|--|--|
| quoteId | string | Id of quote. |
| documentId | string | Id of document. |
| documentName | string | Document name setted on upload. |
| fileName | string | File name. |
| mimeType | string | Mime type. |
| fileSize | long | File size in bytes. |
| createdAt | datetime | Creation UTC. |
