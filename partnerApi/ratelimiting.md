# Rate Limiting 
We use a fixed window algorithm to limit the consumption of API resources.

## Per client configuration:
 - **Read** (generally GET requests) 200 requests per 1 minute
 - **Write** (generally POST requests) 100 requests per 1 minute

### Throttling
You will receive standard ```429``` errors if your calls are being throttled.
