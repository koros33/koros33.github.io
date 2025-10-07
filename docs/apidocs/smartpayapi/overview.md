## **SmartPay API Documentation**

# SmartPay API – Overview

### Introduction

The **SmartPay API** enables developers to integrate secure and seamless digital payments into their applications. With SmartPay, businesses can accept payments globally, verify transactions, issue refunds, and manage real-time payment data, all through a simple REST interface.

SmartPay is built with **speed**, **security**, and **developer experience** in mind, offering predictable JSON responses, easy authentication, and clear documentation inspired by PayPal and Stripe.

**Fictional API Notice**
> The SmartPay API is a **fictional/sample** payments API created for learning, documentation practice, and portfolio demonstration purposes only.  
> It is **not** a live payment processor and does **not** process real payments. Any example keys, webhooks, transaction IDs, or sandbox endpoints in this documentation are illustrative. Do **not** use this API for real financial transactions. For production payment integrations, consult a licensed payment provider such as Stripe, PayPal, or Flutterwave.


### Key Features

*  **Payment Creation** — Initiate transactions with multiple payment methods.
*  **Verification** — Confirm payment status instantly via transaction IDs.
*  **Transaction Management** — Retrieve lists of completed, pending, or failed payments.
*  **Refund Processing** — Easily refund transactions to customers.
*  **Secure Authentication** — Token-based API key system for safe access.
*  **Global Support** — Handle payments in over 100 currencies.



### Base URL

All API requests are made to the base URL below:

```
https://api.smartpay.dev/v1/
```


### Request Format

SmartPay accepts and returns data in **JSON** format.

#### Example Request

```bash
POST /v1/payments
Content-Type: application/json
Authorization: Bearer YOUR_API_KEY
```

#### Example Response

```json
{
  "id": "txn_873451",
  "status": "pending",
  "amount": 2500,
  "currency": "USD"
}
```


### Environments

| Environment    | Base URL                           | Description                                |
| -------------- | ---------------------------------- | ------------------------------------------ |
| **Sandbox**    | `https://sandbox.smartpay.dev/v1/` | Use for testing without real transactions. |
| **Production** | `https://api.smartpay.dev/v1/`     | Live environment for real payments.        |


### Rate Limits

To maintain performance and security, SmartPay enforces the following limits:

* 100 requests per minute per API key.
* Requests beyond the limit return HTTP `429 Too Many Requests`.


### Error Handling

SmartPay uses standard HTTP response codes to indicate API errors.
See [Errors.md](./Errors.md) for details.



### SDKs & Libraries

To simplify integration, SmartPay provides SDKs in:

* JavaScript (Node.js)
* Python
* PHP
* Java

Example libraries:

```bash
npm install smartpay-sdk
pip install smartpay
```



### Support

* 📘 API Reference: [developers.smartpay.dev](https://developers.smartpay.dev)
* 📨 Support: [support@smartpay.dev](mailto:support@smartpay.dev)
* 💬 Community: [community.smartpay.dev](https://community.smartpay.dev)

