# Rate Limiting

> Rate limiting happens on a rolling basis.

Period | Limit
---|---
Minute | Maximum of 120 requests 
Day | Maximum of 86,400 requests (Avg. of 1 per second)

## Unauthenticated

Unauthenticated rate limiting is considered on a per-IP basis.

## Authenticated

Authenticated rate limiting is considered on a per-account basis. Please [contact](mailto:api@buttercoin.com) us if you would like to increase the rate limits for your account.

### HTTP Headers and Response codes

The following headers are included with every API response:

Header | Description
---|---
`X-Rate-Limit-Limit` | The number of requests that can send within your rate limit window 
`X-Rate-Limit-Remaining` | The number of requests that you can send before you will exceed your rate limit 
`X-Rate-Limit-Reset` | When your next rate limit window will be reset (in UTC [epoch milliseconds](http://en.wikipedia.org/wiki/Unix_time))
