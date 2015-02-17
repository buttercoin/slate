# Rate Limiting

> Rate limiting happens on a rolling basis.

Period | Limit
---|---
Minute | Maximum of 120 requests 
rate limiting is considered on a per-IP basis.
> Requests exceeding the limit will receive a '429 Too Many Requests' response. Rate limiting is considered on a per-IP basis.

### HTTP Response Headers

The following headers are applied per minute to public and authenticated requests:

Header | Description
---|---
`X-Rate-Limit-Limit` | The number of requests you can send within your rate limit window 
`X-Rate-Limit-Remaining` | The number of requests that you can send before you will exceed your rate limit 
`X-Rate-Limit-Reset` | When your next rate limit window will be reset (in UTC [epoch milliseconds](http://en.wikipedia.org/wiki/Unix_time))

### Bursting

We allow temporary bursting up to 600 requests per minute. After you submit your first request, you'll find that your `X-Rate-Limit-Remaining` will gradually increate (at 120/minute minus your usage) until it reaches a total of 600. If you do not submit any requests within one hour, it will reset again to 120 requests per minute.
