# Change Quote Status

## Path
/v1/quote/change-status

## Method

POST

## Headers

[require request context](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/authentication.md#request-context)

## Scope
quotas:change-status

## Body
Change Customer Quote Status Request
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| customerQuote | * | [Quote to Convert](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/quote-change-status.md#Quote-for-Change-Status) object |  | Customer quote data for change status serialized as JSON. |



### Quote for Change Status

| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| quoteId | * | string  | max 64 |  Quote identifier|
| statusId | * | [Updatable Property](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/update-quotas.md#updatable-property) |  | Status id value. |

## Valid Request
```
{
	"customerQuote": {
		"quoteId": "629265",
        "statusId": { "oldValue":"2","newValue":"3" }
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
    "traceId": "1e99f720-3f3c-47a5-aeb2-6226af64cd36",
    "errors": {
        "quoteId": [
            "'quoteId' should be a valid id."
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
