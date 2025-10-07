# Authentication

> **Note:** The SmartPay API is a **fictional project** created for technical documentation practice and portfolio use.  
> All endpoints, keys, and examples shown here are for demonstration purposes only — they do not connect to any real payment network.


## Overview

The **SmartPay API** uses **Bearer Token authentication** to ensure secure access to resources.  
Each API request must include a valid **API key** in the request header.  
Keys are generated in the **SmartPay Developer Dashboard** and can be used in either the **sandbox** or **production** environment.


## Authentication Header

Every request must include an `Authorization` header in this format:

```

Authorization: Bearer YOUR_API_KEY

````

### Example
```bash
curl -X GET "https://api.smartpay.dev/v1/payments" \
  -H "Authorization: Bearer sk_live_1a2b3c4d5e6f7g8h" \
  -H "Content-Type: application/json"
````

## Environments

| Environment    | Base URL                           | Description                              |
| -------------- | ---------------------------------- | ---------------------------------------- |
| **Sandbox**    | `https://sandbox.smartpay.dev/v1/` | Test mode for development.               |
| **Production** | `https://api.smartpay.dev/v1/`     | Live mode for real payments (fictional). |

Each environment has a unique API key. Sandbox keys usually begin with `sk_test_`, and production keys with `sk_live_`.


## Obtaining API Keys

1. **Sign up** for a SmartPay Developer Account:
   [https://dashboard.smartpay.dev/signup](https://dashboard.smartpay.dev/signup)

2. **Log in** and go to **Developer → API Keys**.

3. Click **Generate New Key**, then copy your new API key.

4. Store your key securely — do **not** share it publicly or commit it to code repositories.



## Example: Using API Keys (cURL)

```bash
curl -X POST "https://sandbox.smartpay.dev/v1/payments" \
  -H "Authorization: Bearer sk_test_4f3a2b2c1d" \
  -H "Content-Type: application/json" \
  -d '{
        "amount": 1500,
        "currency": "USD",
        "customer_email": "user@example.com"
      }'
```

**Response:**

```json
{
  "id": "txn_1019282",
  "status": "pending",
  "amount": 1500,
  "currency": "USD"
}
```


## Authentication Errors

SmartPay returns standard HTTP status codes when authentication fails.

| Code                      | Error Type               | Description                               |
| ------------------------- | ------------------------ | ----------------------------------------- |
| **401 Unauthorized**      | Invalid API key          | The API key is missing or incorrect.      |
| **403 Forbidden**         | Insufficient permissions | The key lacks the required access scope.  |
| **429 Too Many Requests** | Rate limit exceeded      | Too many requests in a short time period. |

### Example 401 Error Response

```json
{
  "error": {
    "type": "authentication_error",
    "message": "Invalid API key provided."
  }
}
```


## Best Practices

> **Use environment variables** to store your keys securely.

> **Rotate keys** regularly (every 60–90 days).

> **Use least privilege** — assign minimal scopes to each key.

> **Never log keys** or share them via email or screenshots.

**Example (Node.js):**

```js
const apiKey = process.env.SMARTPAY_API_KEY;
```

**Setting the variable (macOS/Linux):**

```bash
export SMARTPAY_API_KEY="sk_test_abc123xyz"
```


## Key Scopes (Optional)

SmartPay supports scoped API keys to limit access:

| Scope             | Description               |
| ----------------- | ------------------------- |
| `payments:read`   | Retrieve payment data     |
| `payments:write`  | Create or update payments |
| `refunds:write`   | Issue refunds             |
| `webhooks:manage` | Configure webhooks        |


## Testing with Sandbox Data

Use the sandbox environment to simulate transactions safely.
Example test cards:

| Card Number           | Behavior                   | Description              |
| --------------------- | -------------------------- | ------------------------ |
| `4242 4242 4242 4242` |  Success                  | Payment succeeds         |
| `4000 0000 0000 0002` |  Declined                 | Card declined            |
| `4000 0000 0000 9995` |  Requires authentication | Simulates 3D Secure flow |

*(For demonstration only — these are fake test numbers.)*


## Troubleshooting

| Issue                     | Possible Fix                                                        |
| ------------------------- | ------------------------------------------------------------------- |
| **401 Unauthorized**      | Check that your API key is correct and not expired.                 |
| **403 Forbidden**         | Verify that the key has the required scopes.                        |
| **429 Too Many Requests** | Wait and retry after the `Retry-After` time in the response header. |


## Example Integration Snippet (Python)

```python
import requests

url = "https://sandbox.smartpay.dev/v1/payments"
headers = {
    "Authorization": "Bearer sk_test_abc123xyz",
    "Content-Type": "application/json"
}
data = {
    "amount": 2000,
    "currency": "KES",
    "customer_email": "demo@user.com"
}

response = requests.post(url, headers=headers, json=data)
print(response.json())
```


