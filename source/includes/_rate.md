# Rate Limiting

> Rate limiting happens on a rolling basis.

Period | Limit
---|---
Minute | Maximum of 120 requests 

> Requests exceeding the limit will receive a '429 Too Many Requests' response.

### HTTP Response Headers

The following headers are applied per minute to public and authenticated requests:

Header | Description
---|---
`X-Rate-Limit-Limit` | The number of requests you can send within your rate limit window 
`X-Rate-Limit-Remaining` | The number of requests that you can send before you will exceed your rate limit 
`X-Rate-Limit-Reset` | When your next rate limit window will be reset (in UTC [epoch milliseconds](http://en.wikipedia.org/wiki/Unix_time))

## Public

Public requests do not require an API key and secret.  Public rate limiting is considered on a per-IP basis.

## Authenticated

Authenticated requests require an API key and secret to access details specific to your account.  Authenticated rate limiting is considered on a per-account basis. Please [contact us](mailto:api@buttercoin.com) if you would like to increase the rate limits for your account.
