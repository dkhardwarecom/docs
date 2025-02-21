# Request Payment for Quote

## Path
/v1/quote/request-payment

## Method

POST

## Headers

[require request context](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/authentication.md#request-context)

## Scope
quotas:request-payment

## Body
Payment for Quote Request
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| customerQuote | * | [Quote for Request Payment](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/request-payment-for-quote.md#quote-for-request-payment) object |  | Customer quote data for request payment serialized as JSON. |
| fraudInsuranceRequired |  | bool |  | Flag for manage fraud insurance. |

### Quote for Request Payment

| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| quoteId | * | string  | max 64 |  Quote identifier|

## Valid Request
```
{
	"customerQuote": {
		"quoteId": "536784"
	},
	"fraudInsuranceRequired":true
}
```

## Success Response

HTTP Status Code: 200

Example:
```
{
    "submissionId": "713dd825-3372-4de0-848a-accda64d4a0b"
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
# Operation Status
Getting quote operation status is the same as [Quote Operation Status](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/orders/create-quotas.md#quote-operation-status) 
