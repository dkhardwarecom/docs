
# Get Vendor Pages

## Path

/v1/vendor/{vendorId}/pages

## Method

POST

## Scope
vendors:pages

## Query Parameters

### Vendor Pages Request
| Name | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| productsIds | * | Array of products ids (string) |  | Products ids |

## Body

[Vendor Pages Request](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/vendors-pages.md#vendors-pages-request) object seralized as JSON.

## Valid Request
```
{
  "productsids":["1600","1"]
}
```

### Success Response

HTTP Status Code: 200

Example:
```
{
    "payload": [
        {
            "productId": "1600",
            "vendorId": "6",
            "productPageUrl": "https://www.crlaurence.com/p/GCB180CH",
            "errors": null,
            "warnings": null
        },
        {
            "productId": "1",
            "vendorId": "6",
            "productPageUrl": "https://www.crlaurence.com/p/PA100D3RPSB",
            "errors": null,
            "warnings": null
        }
    ]
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
    "title": "Request is invalid.",
    "traceId": "20a0efa2-f122-4d05-8c53-e439cf11abd3",
    "errors": {
        "request": [
            "The request field is required."
        ],
        "$.productsids[0]": [
            "The JSON value could not be converted to System.String. Path: $.productsids[0] | LineNumber: 1 | BytePositionInLine: 20."
        ]
    }
}
```

Example for 500:
```
{
    "status": 500,
    "title": "System error.",
    "traceId": "d7234748-ba00-4d69-8cf2-246423cc172c"
}
```

# Contracts

## Payload
Array of [Product Availability](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/vendors-pages.md#vendor-product-pages) 

## Vendor Product Pages
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| productId | * | string | max 64 | Id of product. |
| vendorId | * | string | max 64 | Id of vendor. |
| productPageUrl |  | string | max 2048 | Product page on vendor site URL. |
| errors |  | array of string | | Errors for get current product page operation. |
| warnings |  | array of string | | Warnings for get current product page operation. |



