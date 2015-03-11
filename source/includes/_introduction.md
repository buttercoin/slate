# Introduction

```shell
$ curl -i https://api.buttercoin.com/v1/ticker
HTTP/1.1 200 OK
Content-Type: application/json; charset=UTF-8
X-Rate-Limit-Limit: 120
X-Rate-Limit-Remaining: 119
X-Rate-Limit-Reset: 1424380431341

{
  "currency": "USD",
  "last": 239.69,
  "bid": 239.85,
  "ask": 240.09
}
```

Buttercoin provides developers with a simple and powerful REST API to integrate your applications with our Marketplace, enabling you to deposit and withdraw funds
from your account and execute trades without going through the web interface.

All API access is over HTTPS, and accessed at the [`https://api.buttercoin.com`](https://api.buttercoin.com) domain. All data is sent and received as
JSON - `application/json`.

### Sandbox Environment

To help you test your more complicated workflows, we’ve created a sandbox environment that uses testnet bitcoins and fake funds.
Each Buttercoin API Client allows you to include a sandbox environment parameter during initialization. Please see the API Client
documentation for details.

The web interface for the sandbox is available at [https://www-sandbox.buttercoin.com/](https://www-sandbox.buttercoin.com/).
The API endpoint for the sandbox is [`https://sandbox.buttercoin.com`](https://sandbox.buttercoin.com).