# Authentication

> All clients support the environment variables `BUTTERCOIN_API_KEY` and `BUTTERCOIN_API_SECRET`.

```java
import com.buttercoin.api.*;

Buttercoin buttercoin = Buttercoin.newBuilder()
    .apiKey("pzovcp0kkxmchkuj3smej2wmtjwlare6")
    .apiSecret("KQvYkSZyt0EpJMeKLvMd1sPb1SdrxBqD")
    .build();
```

```ruby
require 'buttercoin'

client = Buttercoin::Client.new(
    :public_key => '<public_key>',
    :secret_key => '<secret_key>'
)
```

```python
from buttercoin.client import ButtercoinClient

client = ButtercoinClient(
    api_key='<api_key>',
    api_secret='<api_secret>'
)
```

```javascript
var buttercoin = require('buttercoin-node')
var client = buttercoin(
    '<api_key>',
    '<api_secret>',
    '<environment>',
    '<version>'
);
```

```php
<?php
require 'vendor/autoload.php';
use Buttercoin\Client\ButtercoinClient;

$client = ButtercoinClient::factory([
    'publicKey' => '<public_key>',
    'secretKey' => '<secret_key>',
    'environment' => '<environment>' 
    ]);
?>
```
> The client will automatically sign your requests with the proper headers. If you are not using a client,
  authenticated requests should include the X-Buttercoin-Access-Key, X-Buttercoin-Signature and X-Buttercoin-Date headers.

The Buttercoin API provides publicly accessible endpoints to get the current ticker price, the current order book, and the trade history.
All other API calls require a valid API Key and API Secret.

<aside class="warning">
Buttercoin will *never* ask you for your API Key or Secret. Please [report](mailto:security@buttercoin.com) to us any emails you receive that
request this information.

You must always keep your API Keys secure to make sure no one can access your account.  If you think a key might be compromised, simply revoke
your API key [here](https://www.buttercoin.com/#/api).
</aside>

### Building an HMAC Signature with SHA-256

1. Concatenate the timestamp, request URL and parameters into a UTF-8 String:
2. Convert the message to Base64
3. Sign the message using HMAC with SHA-256 and your API Secret Key
4. Convert to Base64 once again

Encode a get request like this:

`1403755197367https://api.buttercoin.com/v1/orders?status=filled&orderType=limit`

Encode a post request like this:

`1403755197367https://api.buttercoin.com/v1/orders{"instrument":"BTC_USD","side":"buy","orderType":"limit","quantity":1,"price":600.01}`

### HTTP Headers

`X-Buttercoin-Access-Key: <your API Key>`

`X-Buttercoin-Signature: <the HMAC signature>`

`X-Buttercoin-Date: <the current date epoch`