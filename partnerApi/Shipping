# Get Shipping Rates

## Path

/v1/shipping/rates

## Method

POST

## Scope
shipping

## Query Parameters

### Request
| Name | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| OrderItems| * | Array of [Order Item]|  | Order items with id and quantity |
| DeliveryAddress | * |Complex type [Country and State Delivery Address]  |  | Address to delivery |
| OrderSubTotal |  | Money | | Amount of order subtotal |

### Country and State Delivery Address
| Name | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| Country | * | string(2)|  | Country code. For example: "US" for USA, "IN" for India, "RU" for Russian Federation. |
| StateCode |  | string(?)  |  | Code of region. |

### Order Item
| Name | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| ProductId | * | long integer |  | Id of product. |
| Quantity | * | integer  |  | Quantity to order. |
