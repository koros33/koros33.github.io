# Errors

The OpenWeather API uses standard HTTP status codes to indicate the success or failure of a request.  
When an error occurs, the response body includes a JSON object with details.


## Error Format

All errors follow this structure:

```json
{
  "code": "404",
  "message": "city not found"
}
```

## Common Status Codes

| Code    | Meaning               | Example Message                      | When It Happens                   |
| ------- | --------------------- | ------------------------------------ | --------------------------------- |
| **200** | OK                    | —                                    | Request succeeded                 |
| **400** | Bad Request           | "Nothing to geocode"                 | Missing or invalid parameters     |
| **401** | Unauthorized          | "Invalid API key"                    | API key missing or incorrect      |
| **404** | Not Found             | "city not found"                     | Requested location does not exist |
| **429** | Too Many Requests     | "You have exceeded your daily limit" | Rate limit exceeded               |
| **500** | Internal Server Error | "Unexpected error"                   | Server-side issue (rare)          |


##  Example Responses

### 401 Unauthorized

```json
{
  "code": 401,
  "message": "Invalid API key. Please see http://openweathermap.org/faq#error401"
}
```

### 404 City Not Found

```json
{
  "code": "404",
  "message": "city not found"
}
```

### 429 Rate Limited

```json
{
  "code": 429,
  "message": "Your account is temporarily blocked due to exceeding the requests limit."
}
```


##  Handling Errors in Your App

1. **Check HTTP status codes** before processing the response.
2. **Retry logic**: For 500 or 429 errors, implement exponential backoff.
3. **Validate inputs**: Ensure city names, coordinates, and zip codes are valid.
4. **Secure your API key** to avoid unauthorized usage.



##  FAQs

**Q: What happens if I exceed my free tier limit?**
A: You’ll receive a `429 Too Many Requests` error until your quota resets.

**Q: Can I ignore the `cod` field and just check HTTP codes?**
A: It’s best to use **both** sometimes error details are only in the JSON body.

**Q: Do errors count against my API limit?**
A: Yes, every request (successful or failed) counts toward your quota.
