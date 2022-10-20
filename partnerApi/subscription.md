
# Get Subscriptions

## Path
/v1/subscription/

## Method

GET

## Scope
subscriptions

## Query Parameters
| Name | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| from|  | DateTime| default(null)<br />UTC | From updated (or created) date and time filter value.<br /> Example: /v1/customer?from=2022-03-11T22:15:59Z |
| to|  | DateTime| default(null)<br />UTC | To updated (or created) date and time filter value.<br /> Example: /v1/customer?to=2022-03-13T10:45:11Z |
| eventType |  | string| max 64  | Type of event. For example: 'customer:changed'. |
| actionType |  | enum | values: webhook,...  | Type of subscription action. For example: webhook url call. |
| newest|  | Boolean| default(true) | If true, return in descending order newest to oldest. |
| limit|  | integer | max 1000, default(100) | Return a number of records with the set limit value. |
| offset |  | integer | default(0) | Return a subset of records starting with the offset value. |
| basedOnCreatedDate|  | Boolean | default(false) | If true, return subset based on created date else updated date |

## Success Response

HTTP Status Code: 200

Example:
```
{
	"payload": [
		{
			"webhook": {
				"secret": "40158583e9bd9d122014907b57a60c12",
				"url": "https://some.site/webhook"
			},
			"enentType": "customer:changed",
			"actionType": "webhook",
			"policies": {
				"retry": {
					"intervals": [
						{
							"value": "00:01:07"
						}
					]
				}
			},
			"createdAt": "2022-10-20T11:15:45.2397901Z",
			"updatedAt": "2022-10-20T11:15:45.2398178Z",
			"subscriptionId": "bbd76e0b-b14e-4610-b307-041fd4cfdfa4"
		}
	]
}
                ...
```

## Error Response

| HTTP status code | Message |
|--|--|
| 400 |  |
| 500 |  |
|  |  |


# Get Subscription by Id

## Path
/v1/subscription/{subscriptionId}

## Method

GET

## Scope
subscriptions

## Success Response

HTTP Status Code: 200

Example:
```
{
	"payload": {
		"webhook": {
			"secret": "40158583e9bd9d122014907b57a60c12",
			"url": "https://some.site/webhook"
		},
		"enentType": "customer:changed",
		"actionType": "webhook",
		"policies": {
			"retry": {
				"intervals": [
					{
						"value": "00:01:07"
					}
				]
			}
		},
		"createdAt": "0001-01-01T00:00:00",
		"updatedAt": "0001-01-01T00:00:00",
		"subscriptionId": "bbd76e0b-b14e-4610-b307-041fd4cfdfa4"
	}
}
```

## Error Response


| HTTP status code | Message |
|--|--|
| 400 |  |
| 500 |  |
| 404 |  |

# Create Subscription

## Path
/v1/subscription/create

## Method

POST

## Scope
subscriptions:edit

## Body

[Subscription](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/subscription.md#subscription-base) contract serialized as json.

## Valid Request
```
{
	"webhook": {
		"secret": "40158583e9bd9d122014907b57a60c12",
		"url": "https://some.site/webhook"
	},
	"enentType": "customer:changed",
	"actionType": "webhook",
	"policies": {
		"retry": {
			"intervals": [
				{
					"value": "00:00:30"
				},
				{
					"value": "00:02:00"
				}
			]
		}
	}
}
```

## Success Response

HTTP Status Code: 200

Example:
```
{
    "subscriptionId": "77921d3a-7838-40bf-a2d2-e30424d15520"
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

```

Example for 500:
```
{
    "status": 500,
    "title": "System error.",
    "traceId": "d7234748-ba00-4d87-8cf2-246423cc172c"
}
```

# Update Subscription

## Path
/v1/subscription/update

## Method

POST

## Scope
Subscriptions:edit

## Body

[Subscription](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/subscription.md#subscription-base) contract serialized as json.

## Valid Request
```
{
	"subscriptionId": "bbd76e0b-b14e-4610-b307-041fd4cfdfa4",
	"webhook": {
		"secret": "40158583e9bd9d122014907b57a60c12",
		"url": "https://some-other.site/webhook"
	},
	"enentType": "customer:changed",
	"actionType": "webhook",
	"policies": {
		"retry": {
			"intervals": [
				{
					"value": "00:00:20"
				}
			]
		}
	}
}
```

## Success Response

HTTP Status Code: 200

Example:
```
{
    "subscriptionId": "bbd76e0b-b14e-4610-b307-041fd4cfdfa4"
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

```

Example for 500:
```
{
    "status": 500,
    "title": "System error.",
    "traceId": "3a6a590a-1263-4fb0-a330-82e9e62c13c9"
}
```

# Delete Subscription

## Path
/v1/subscription/delete

## Method

POST

## Scope
subscriptions:edit

## Body

SubscriptionId serialized as json.

| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| SubscriptionId | * | string | max 64 | Identifier of subscription for delete. |

## Valid Request
```
{
     "subscriptionId": "bbd76e0b-b14e-4610-b307-041fd4cfdfa4"
}
```

## Success Response

HTTP Status Code: 200

Example:
```
{
     "subscriptionId": "bbd76e0b-b14e-4610-b307-041fd4cfdfa4"
}
```

Example with errors messages:
```

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
    "traceId": "3a6a590a-1263-4fb0-a330-82e9e62c13c9"
}
```



# Contracts

### Subscription Base
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| subscriptionId | * | string | max 64 | Identifier of subscription |
| enentType | * | string | max 64 | Type of event. For example: 'customer:changed'. |
| actionType | * | enum | values: webhook,...  | Type of subscription action. For example: webhook url call. |
| policies |  |Complex type [Subscription Policies](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/subscription.md#subscription-policies)  |  | Some behaviour policies for Subscription. |
| createdAt |  | dateTime |  | Creation date and time in UTC format |
| updatedAt |  | dateTime |  | Updated date and time in UTC format |

### Subscription Policies
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| Retry | * |Complex type [RetryPolicy](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/subscription.md#retry-policy)  |  | Retry policy settings. |

### Retry Policy
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| Intervals | * |Array of [RetryPolicyInterval](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/subscription.md#retry-policy-interval)  |  | Retry policy settings. |

### Retry Policy Interval
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| Value | * | time span  |  | Value of interval. For example '02:10:30' for 2 hours 10 minutes and 30 seconds.  |

### Webhook Action Subscription
Specific for webhook action:

| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| Webhook | * |Complex type [Webhook](https://github.com/dkhardwarecom/docs/blob/main/partnerApi/subscription.md#webhook)  |  | Webhook settings. |

### Webhook
| Field | Required | Type | Restrictions | Description |
|--|--|--|--|--|
| Url | * | string  | max 1024 https only | Url for HTTP POST call. Normalized url. Https required. |
| Secret | * | string  | max 64 | Secret string shared for webhook url caller and subscription creator. Sent as part of https POST request. |

