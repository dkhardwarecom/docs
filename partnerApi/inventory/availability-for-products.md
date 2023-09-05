
# Availability for Products

## Path

/v1/inventory/availability/for-products

## Method

POST

## Scope
innventory:availability

## Query Parameters

### Availability for Products Request
| Name | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| productsIds | * | Array of products ids (string) |  | Products ids |

## Body

[Availability for Products Request](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/inventory/availability-for-products.md#availability-for-products-request) object seralized as JSON.

## Valid Request
```
{
  "productsids":["600","700"]
}
```

### Success Response

HTTP Status Code: 200

Example:
```
{
    "payload": {
        "availability": [
            {
                "productId": "600",
                "vendorsStock": [
                    {
                        "warehouseId": "1",
                        "own": 7,
                        "total": 7
                    },
                    {
                        "warehouseId": "5",
                        "own": 1,
                        "total": 1
                    },
                    {
                        "warehouseId": "13",
                        "own": 1,
                        "total": 1
                    },
                    {
                        "warehouseId": "359",
                        "total": 61
                    },
                    {
                        "warehouseId": "424",
                        "total": 35
                    },
                    {
                        "warehouseId": "425",
                        "total": 137
                    },
                    {
                        "warehouseId": "426",
                        "total": 34
                    },
                    {
                        "warehouseId": "428",
                        "total": 56
                    },
                    {
                        "warehouseId": "432",
                        "total": 67
                    },
                    {
                        "warehouseId": "433",
                        "total": 107
                    },
                    {
                        "warehouseId": "435",
                        "total": 113
                    },
                    {
                        "warehouseId": "436",
                        "total": 90
                    },
                    {
                        "warehouseId": "437",
                        "total": 15
                    },
                    {
                        "warehouseId": "440",
                        "total": 108
                    },
                    {
                        "warehouseId": "490",
                        "total": 100
                    },
                    {
                        "warehouseId": "491",
                        "total": 27
                    },
                    {
                        "warehouseId": "471",
                        "total": 34
                    },
                    {
                        "warehouseId": "576",
                        "total": 37
                    },
                    {
                        "warehouseId": "577",
                        "total": 2
                    }
                ],
                "aggregatedStock": {
                    "local": {
                        "total": 0
                    },
                    "vendor": {
                        "own": 9,
                        "total": 1032
                    },
                    "all": {
                        "own": 9,
                        "total": 1032
                    }
                }
            },
            {
                "productId": "700",
                "localStock": [
                    {
                        "warehouseId": "1",
                        "own": 2,
                        "total": 2
                    }
                ],
                "aggregatedStock": {
                    "local": {
                        "own": 2,
                        "total": 2
                    },
                    "vendor": {
                        "total": 0
                    },
                    "all": {
                        "own": 2,
                        "total": 2
                    }
                }
            }
        ]
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
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
|  availability |  | Array of [Product Availability](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/inventory/availability-for-products.md#product-availability) | | Availability data |

## Product Availability
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| productId | * | string | max 64 | Id of product. |
| localStock |  | Array of [Warehouse Stock](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/inventory/availability-for-products.md#warehouse-stock) | | Local warehouses stock data |
| vendorStock |  | Array of [Warehouse Stock](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/inventory/availability-for-products.md#warehouse-stock) | | Vendor warehouses stock data |
| aggregatedStock | * | [Aggregated Stock](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/inventory/availability-for-products.md#aggregated-stock) | | Aggregated stock data |

## Warehouse Stock
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| warehouseId | * | string | max 8 | Id of warehouse. |
| own |  | int |  | Own stock count. Stock count **exclude** compounds and equivalences products stock count.  |
| total | * | int |  | Total stock count. Stock count **include** compounds and equivalences products stock count. |

## Aggregated Stock
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| local |  | [Stock](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/inventory/availability-for-products.md#stock) |  |  Local warehouses stock counts.  |
| vendor |  | [Stock](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/inventory/availability-for-products.md#stock) |  | Vendor warehouses stock counts.  |
| all |  | [Stock](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/inventory/availability-for-products.md#stock) |  | All warehouses stock counts.  |

## Stock
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| own |  | int |  | Own stock count. Stock count **exclude** compounds and equivalences products stock count.  |
| total | * | int |  | Total stock count. Stock count **include** compounds and equivalences products stock count. |

# Releases
-------------------------------
| Date | Version |
|--|--|
| 2023 September 5 | 20230905.2 |
### Release Notes

* Availability for products endpoint added.

