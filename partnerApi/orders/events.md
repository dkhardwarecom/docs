# Events

## Quote Changed

### Id
customer-quote:changed

### Payload
| Field | Type | Description |
|--|--|--|
| quoteIds | Array of string | Identifiers of changed quotas.  |
| date |  date and time | UTC date of changes. |

Example:
```
{
	"event": "customer-quote:changed",
	"secret": "78f1a65ff4cc4d8ab6b855cd3c15ff79",
	"payload": {
		"quoteIds": [
			"6781345",
			"6781346"
		],
		"date":"2023-01-20T10:45:15Z"
	}
}
```
## Order Changed

### Id
customer-order:changed

### Payload
| Field | Type | Description |
|--|--|--|
| orderIds | Array of string | Identifiers of changed orders.  |
| date |  date and time | UTC date of changes. |

Example:
```
{
	"event": "customer-order:changed",
	"secret": "78f1a65ff4cc4d8ab6b855cd3c15ff79",
	"payload": {
		"orderIds": [
			"6771377",
			"6771378"
		],
		"date":"2023-01-20T10:45:15Z"
	}
}
```

## RMA Changed

### Id
customer-return:changed

### Payload
| Field | Type | Description |
|--|--|--|
| returnIds | Array of string | Identifiers of changed RMAs.  |
| date |  date and time | UTC date of changes. |

Example:
```
{
	"event": "customer-return:changed",
	"secret": "78f1a65ff4cc4d8ab6b855cd3c15ff79",
	"payload": {
		"returnIds": [
			"7771377",
			"7771378"
		],
		"date":"2023-01-20T10:45:15Z"
	}
}
```

## Vendor Quote Changed

### Id
vendor-quote:changed

### Payload
| Field | Type | Description |
|--|--|--|
| quoteIds | Array of string | Identifiers of changed vendor quotas.  |
| date |  date and time | UTC date of changes. |

Example:
```
{
	"event": "vendor-quote:changed",
	"secret": "78f1a65ff4cc4d8ab6b855cd3c15ff79",
	"payload": {
		"quoteIds": [
			"5781343",
			"5781344"
		],
		"date":"2023-01-20T10:45:15Z"
	}
}
```
## Vendor Order Changed

### Id
vendor-order:changed

### Payload
| Field | Type | Description |
|--|--|--|
| orderIds | Array of string | Identifiers of changed vendor orders.  |
| date |  date and time | UTC date of changes. |

Example:
```
{
	"event": "vendor-order:changed",
	"secret": "78f1a65ff4cc4d8ab6b855cd3c15ff79",
	"payload": {
		"orderIds": [
			"57715467",
			"57713943"
		],
		"date":"2023-01-20T10:45:15Z"
	}
}
```

## Vendor RMA Changed

### Id
vendor-return:changed

### Payload
| Field | Type | Description |
|--|--|--|
| returnIds | Array of string | Identifiers of changed vendor RMAs.  |
| date |  date and time | UTC date of changes. |

Example:
```
{
	"event": "vendor-return:changed",
	"secret": "78f1a65ff4cc4d8ab6b855cd3c15ff79",
	"payload": {
		"returnIds": [
			"9771311",
			"9771378"
		],
		"date":"2023-01-20T10:45:15Z"
	}
}
```
