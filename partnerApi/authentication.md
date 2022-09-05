# Authentication

## Getting an Access Token

We use the Client Credentials Grant Flow, which allows an application to request an Access Token using only its App ID and App Secret. With this flow, you still need credentials and permission from a user to call services on their behalf. Refresh tokens are used to get a new access token when your current access token expires. By default, access tokens are valid for 60 days and programmatic refresh tokens are valid for a year. The member must reauthorize your application when refresh tokens expire.

### Authorization Flow
1. Get `client_id` and `client_secret` from DK Hardware team
2. Call `https://auth.dkhardware.com/realms/dkh/protocol/openid-connect/token` endpoint
3. If the call is successful, the endpoint returns an `access_token` and `refresh_token`.

### Header Parameters

| name | value |
|--|--|
| Content-Type | application/x-www-form-urlencoded |

### Data Parameters
| name | value |
|--|--|
| client_id | your `client_id`  |
| client_secret | your `client_secret`  |
| grant_type | client_credentials  |
| scope | available `scopes` divided by ` ` (space) |

Example of available scopes: `customers orders returns vendor-orders`

### Response example

```
{
    "access_token": "eyJhbGciOiJSUzI1NiIsInR5cCIgOiAiSldUIiwia2lkIiA6ICJZeG5oc0RtSkVWSlMyTWRfS0tTOVIteHVMbTUtZEtYN2ZXaFZKWGlNMVFnIn0.eyJleHAiOjE2NTk2MjExMjgsImlhdCI6MTY1OTYxNTcyOCwianRpIjoiMzM2MWQ5YjktN2VmMC00ZTk2LWEwMDQtYzgzMmZhZWJiODI1IiwiaXNzIjoiaHR0cHM6Ly9rZXljbG9hay5zdGFnaW5nLmRraGRldi5jb20vcmVhbG1zL0RLSCIsImF1ZCI6ImFwaTovL2FwaS5ka2hhcmR3YXJlLmNvbSIsInN1YiI6ImI3MzliNGMwLTA1M2QtNDVhZC1hMzg1LWNjNTZmZDljZmU1NyIsInR5cCI6IkJlYXJlciIsImF6cCI6InBhcnRuZXItYXBpIiwic2Vzc2lvbl9zdGF0ZSI6IjgxM2QzNTZhLTE2NGUtNGM4MS04OTliLTNiODVlMTAyNWQxMSIsInNjb3BlIjoiY3VzdG9tZXJzIiwic2lkIjoiODEzZDM1NmEtMTY0ZS00YzgxLTg5OWItM2I4NWUxMDI1ZDExIiwiY2xpZW50SG9zdCI6IjEwLjAuMC4xMCIsImNsaWVudElkIjoicGFydG5lci1hcGkiLCJjbGllbnRBZGRyZXNzIjoiMTAuMC4wLjEwIn0.kdvb266w0k9hhyKpf3JDtxT72RTNtpFjPMcf7O89sQuU1A6gPk-4qpUF7xZ2Ie5_juw7J8RX5HxsK8W2xoTZVaYiqWd7QtFYpYPz8JXkKcA98WeSmyTqjd-abqOHA-myK6BzaF8e3h7yjxsUNyeRWp0YvqhpeU0FFp872hSck-h1oNUuIsGxzn_Lp4yyHYcpEDbdR0LzW7b8zOicCvhHatFe6Ao2hPIywiqdXorTmX6bcfW2CrbY8v1DrzHpL4N_dwolTjDKPV3nTHMOsUuc-Y1R_15wB1EeyITYYIWZk2-GcdAwiYcixDSgGkolWA79pR-EIQsDg35EoGCaV0NaGw",
    "expires_in": 5400,
    "refresh_expires_in": 18000,
    "refresh_token": "eyJhbGciOiJIUzI1NiIsInR5cCIgOiAiSldUIiwia2lkIiA6ICJhOWUxZDIyYy0yNGMzLTRiNWEtOTExZi04NmU3OTk0ODVkY2EifQ.eyJleHAiOjE2NTk2MTc1MjgsImlhdCI6MTY1OTYxNTcyOCwianRpIjoiZjE5NDllYWItMjcwMC00MjZhLWE3ZjUtYTM2MWYzOTk1MjUyIiwiaXNzIjoiaHR0cHM6Ly9rZXljbG9hay5zdGFnaW5nLmRraGRldi5jb20vcmVhbG1zL0RLSCIsImF1ZCI6Imh0dHBzOi8va2V5Y2xvYWsuc3RhZ2luZy5ka2hkZXYuY29tL3JlYWxtcy9ES0giLCJzdWIiOiJiNzM5YjRjMC0wNTNkLTQ1YWQtYTM4NS1jYzU2ZmQ5Y2ZlNTciLCJ0eXAiOiJSZWZyZXNoIiwiYXpwIjoicGFydG5lci1hcGkiLCJzZXNzaW9uX3N0YXRlIjoiODEzZDM1NmEtMTY0ZS00YzgxLTg5OWItM2I4NWUxMDI1ZDExIiwic2NvcGUiOiJjdXN0b21lcnMiLCJzaWQiOiI4MTNkMzU2YS0xNjRlLTRjODEtODk5Yi0zYjg1ZTEwMjVkMTEifQ._9lHZCn1DtWUt7etO3V3sMqgZJxRSL-jnji-qv4CW5o",
    "token_type": "Bearer",
    "not-before-policy": 0,
    "session_state": "813d356a-164e-4c81-899b-3b85e1025d11",
    "scope": "customers"
}
``` 


## Using Access Token
Once you have an Access Token, you can use it to call authorized APIs. You can do this by placing your Access Token in the Authorization header prepended with `Bearer `.


## Using a Refresh Token



 
