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
| OrderItems| * | Array of [Order Item](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/shipping.md#order-item) |  | Order items with id and quantity |
| DeliveryAddress | * |Complex type [Country and State Delivery Address](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/shipping.md#country-and-state-delivery-address)  |  | Address to delivery |
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
