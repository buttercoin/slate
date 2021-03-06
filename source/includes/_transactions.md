# Transactions

Transactions are deposits and withdrawals of fiat currency and bitcoin.

## Get all transactions 

```ruby
query = { "status" => "opened" }
client.get_transactions(query)
```

```python
query = {'status': 'filled'}
client.get_transactions(body=query)
```

```javascript
var query = { side: 'sell' };
client.getTransactions(query, function (err, transactions) {
  console.log("transactions err", err);
  console.log("transactions", transactions);
});
```

```php
<?php
$query = [ "status" => "canceled", "side" => "sell" ];
$client->getTransactions($query);
?>
```

```ruby
# Hashie::Mash Object
transactions.each do |transaction|
transaction.transactionId # "538bdc82848a604c007ceac6"
transaction.status # "open"
transaction.events.each do |event|
event.eventType
event.eventDate
end
end
```

```python
[
  {
    "transactionId": "538bdc82848a604c007ceac6",
    "transactionType": "deposit",
    "currency": "USD",
    "amount": 500.98,
    "method": "wire",
    "status": "funded",
    "fundingInfo": {
      "source": "External Customer Bank"
    },
    "events": [
      {
        "eventType": "created",
        "eventDate": "2014-05-06T13:15:30Z"
      }
    ]
  }
]
```

```javascript
[
  {
    "transactionId": "538bdc82848a604c007ceac6",
    "transactionType": "deposit",
    "currency": "USD",
    "amount": 500.98,
    "method": "wire",
    "status": "funded",
    "fundingInfo": {
      "source": "External Customer Bank"
    },
    "events": [
      {
        "eventType": "created",
        "eventDate": "2014-05-06T13:15:30Z"
      }
    ]
  }
]
```

```php
<?php
[
  {
    "transactionId": "538bdc82848a604c007ceac6",
    "transactionType": "deposit",
    "currency": "USD",
    "amount": 500.98,
    "method": "wire",
    "status": "funded",
    "fundingInfo": {
      "source": "External Customer Bank"
    },
    "events": [
      {
        "eventType": "created",
        "eventDate": "2014-05-06T13:15:30Z"
      }
    ]
  }
]
?>
```

This endpoint retrieves all transactions based on the given query.

### HTTP Request

`GET /v1/transactions`

### Query Parameters

Parameter | Description
--- | ---
`page` | Integer
`pageSize` | Integer
`status` | enum: `['pending', 'processing', 'funded', 'canceled', 'failed']`  
`transactionType` | enum: `['deposit', 'withdrawal']`  
`dateMin` | format: ISO-8601, e.g. `'2014-05-06T13:15:30Z'`  
`dateMax` | format: ISO-8601, e.g. `'2014-05-06T13:15:30Z'`

### Paging

Use `page` and `pageSize` parameters to retrieve additional transaction results. The default `page` parameter value is 1 if not provided. The default `pageSize` parameter value is 20 if not provided.

The response will include an `X-Next-Page-Url` header with the URL to request the next page of transaction results.

## Get a single transaction

```ruby
# Get transaction with the ID
transaction_id = '538bdc82848a604c007ceac6'
client.get_transaction_by_id(transaction_id)

# For convenience, you can also get transaction by full URL
url = 'https://api.buttercoin.com/v1/transactions/538bdc82848a604c007ceac6'
client.get_transaction_by_url(url)
  ```

```python
# Get transaction with the ID
transaction_id = '538bdc82848a604c007ceac6'
client.get_transaction_by_id(transaction_id)

# For convenience, you can also get transaction by full URL
url = 'https://api.buttercoin.com/v1/transactions/538bdc82848a604c007ceac6'
client.get_transaction_by_url(url)
```

```javascript
// Get transaction with the ID
var transactionId = '538bdc82848a604c007ceac6';
client.getTransactionById(transactionId, function (err, transaction) {
  console.log("transaction err", err);
  console.log("transaction", transaction);
});

// For convenience, you can also get transaction by full URL
var url = 'https://api.buttercoin.com/v1/transactions/538bdc82848a604c007ceac6';
client.getTransactionByUrl(url, function (err, transaction) {
  console.log("transaction err", err);
  console.log("transaction", transaction);
});
```

```php
<?php
// Get transaction with the ID
$transactionId = '538bdc82848a604c007ceac6';
$client->getTransactionById($transactionId);

// For convenience, you can also get transaction by full URL
$url = 'https://api.buttercoin.com/v1/transactions/538bdc82848a604c007ceac6';
$client->getTransactionByUrl($url);
?>
```

```ruby
# Hashie::Mash Object
transaction.transactionId # "538bdc82848a604c007ceac6"
transaction.status # "open"
transaction.events.each do |event|
event.eventType
event.eventDate
end
```

```python
# Dict Object
{
  "transactionId": "538bdc82848a604c007ceac6",
  "transactionType": "deposit",
  "currency": "USD",
  "amount": 500.98,
  "method": "wire",
  "status": "funded",
  "fundingInfo": {
    "source": "External Customer Bank"
  },
  "events": [
    {
      "eventType": "created",
      "eventDate": "2014-05-06T13:15:30Z"
    }
  ]
}
```

```javascript
// Json Object
{
  "transactionId": "538bdc82848a604c007ceac6",
  "transactionType": "deposit",
  "currency": "USD",
  "amount": 500.98,
  "method": "wire",
  "status": "funded",
  "fundingInfo": {
    "source": "External Customer Bank"
  },
  "events": [
    {
      "eventType": "created",
      "eventDate": "2014-05-06T13:15:30Z"
    }
  ]
}
```

```php
<?php
// Array Object
[
  "transactionId" => "538bdc82848a604c007ceac6",
  "transactionType" => "deposit",
  "currency" => "USD",
  "amount" => 500.98,
  "method" => "wire",
  "status" => "funded",
  "fundingInfo" => {
    "source": "External Customer Bank"
  },
  "events" => [
    [
      "eventType" => "created",
      "eventDate" => "2014-05-06T13:15:30Z"
    ]
  ]
]
?>
```

This endpoint retrieves a single transaction with the given ID.

### HTTP Request

`GET /v1/transactions/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the transaction to retrieve

## Create a deposit

```ruby
deposit = { 
  :method => "wire",
  :currency => "USD",
  :amount => "500"
}

client.create_deposit(deposit)
```

```python
deposit = {
  method: "wire",
  currency: "USD",
  amount: "5002"
}

client.create_deposit(deposit)
```

```javascript
var deposit = {
  method: "wire",
  currency: "USD",
  amount: "5002"
};

client.createDeposit(deposit, function (err, msg) {
  console.log("cancel transaction err", err);
  console.log("cancel transaction", msg);
});
```

```php
<?php
$deposit = [
  "method" => "wire",
  "currency" => "USD",
  "amount" => "500"
];

$client->createDeposit($deposit);
?>
```

> A successful deposit transaction creation returns the url location of the new transaction in the response location header with HTTP Response Code of 202.

```ruby
# string
'https://api.buttercoin.com/v1/transactions/538bdc82848a604c007ceac6'
```

```python
# string
'https://api.buttercoin.com/v1/transactions/538bdc82848a604c007ceac6'
```

```javascript
// string
'https://api.buttercoin.com/v1/transactions/538bdc82848a604c007ceac6'
```

```php
<?php
// string
'https://api.buttercoin.com/v1/transactions/538bdc82848a604c007ceac6'
?>
```

Create a new deposit with the given params

Parameter | Description
--- | ---
`method` | enum: `['wire']`, required `true`  
`currency` | enum: `['USD']`, required `true`  
`amount` | `string`, required `true`

<aside class="info">
Please contact Buttercoin support before creating a USD deposit using the API.
</aside>

### HTTP Request

`POST /v1/transactions/deposit`

## Create a withdrawal

```ruby
withdrawal = {
  :method => "us_ach",
  :currency => "USD",
  :amount => "500"
}
client.create_withdrawal(withdrawal)
```

```python
withdrawal = {
  "currency": "USD",
  "amount": "30020.30",
  "method": "us_ach" 
}
client.create_transaction(withdrawal)
  ```

```javascript
var withdrawal = {
  "currency": "USD",
  "amount": "30020.30",
  "method": "us_ach" 
};
client.createWithdrawal(withdrawal, function (err, msg) {
  console.log("cancel transaction err", err);
  console.log("cancel transaction", msg);
});
```

```php
<?php
$withdrawal = [
  "method" => "us_ach",
  "currency" => "USD",
  "amount" => "500"
];
$client->createWithdrawal($withdrawal);
?>
```

> If you have the security setting requiring confirmation for withdrawal, you will see this message requiring further action with HTTP Response Code of 201:

```ruby
# Hashie::Mash
response.status # 201
response.message # This operation requires email confirmation
```

```python
{ "status": 201, "message": 'This operation requires email confirmation' }
```

```javascript
{ status: 201, message: 'This operation requires email confirmation' }
```

```php
<?php
[ 'status' => 201, 'message' => 'Withdraw request created, but email confirmation is required' ]
?>
```

> A successful withdrawal transaction creation returns the url location of the new transaction in the response location header with HTTP Response Code of 202.

```ruby
# string
'https://api.buttercoin.com/v1/transactions/538bdc82848a604c007ceac6'
```

```python
# string
'https://api.buttercoin.com/v1/transactions/538bdc82848a604c007ceac6'
```

```javascript
// string
'https://api.buttercoin.com/v1/transactions/538bdc82848a604c007ceac6'
```

```php
<?php
// string
'https://api.buttercoin.com/v1/transactions/538bdc82848a604c007ceac6'
?>
```

Create a new withdrawal with the given params

Parameter | Description
--- | --- 
`method` | enum: `['us_ach']`, required `true`  
`currency` | enum: `['USD']`, required `true`  
`amount` | `string`, required `true`

### HTTP Request

`POST /v1/transactions/withdraw`

<aside class="info">
For your security, the default setting for withdrawals requires email confirmation. You can view or change this setting [here](https://buttercoin.com/#/settings#tab-notifications).
</aside>

## Send bitcoins

```ruby
trxn = {
  :currency => "BTC",
  :amount => "100.231231",
  :destination => "<bitcoin_address>"
}

client.send_bitcoin(trxn)
```

```python
txn = {
  "currency": "BTC",
  "amount": "0.30", 
  "destination": "<bitcoin_address>"
}
client.send_bitcoin(txn)
```

```javascript
var txn = {
  "currency": "BTC",
  "amount": "0.30", 
  "destination": "<bitcoin_address>"
};
client.sendBitcoin(txn, function (err, msg) {
  console.log("send bitcoin err", err);
  console.log("send bitcoin", msg);
});
```

```php
<?php
$trxn = {
  "currency" => "BTC",
  "amount" => "100.231231",
  "destination" => "<bitcoin_address>"
};
$client->sendCrypto($trxn);
?>
```

> If you have the security setting requiring confirmation for bitcoin withdrawal, you will see this message requiring further action with HTTP Response Code of 201:

```ruby
# Hashie::Mash
response.status # 201
response.message # This operation requires email confirmation
```

```python
{ "status": 201, "message": 'This operation requires email confirmation' }
```

```javascript
{ status: 201, message: 'This operation requires email confirmation' }
```

```php
<?php
[ 'status' => 201, 'message' => 'Send request created, but email confirmation is required' ]
?>
```

> A successful withdrawal transaction creation returns the url location of the new transaction in the response location header with HTTP Response Code of 202.

```ruby
# string
'http://api.buttercoin.com/v1/transactions/538bdc82848a604c007ceac6'
```

```python
# string
'https://api.buttercoin.com/v1/transactions/538bdc82848a604c007ceac6'
```

```javascript
// string
'https://api.buttercoin.com/v1/transactions/538bdc82848a604c007ceac6'
```

```php
<?php
// string
'https://api.buttercoin.com/v1/transactions/538bdc82848a604c007ceac6'
?>
```

Send bitcoins to the given address with the following params params

Parameter | Description
--- | --- 
`currency` | enum: `['BTC']`, required `true`  
`amount` | `string`, required `true`  
`destination` | address to which to send currency `string`, required `true`

### HTTP Request

`POST /v1/transactions/send`

<aside class="info">
For your security, the default setting for withdrawals requires email confirmation. You can view or change this setting [here](https://buttercoin.com/#/settings#tab-notifications).
</aside>

## Cancel a transaction

```ruby
  transaction_id = 'e3afed81-4a9c-4480-a78a-e0872408b95a'
client.cancel_transaction(transaction_id)
```

```python
transaction_id = 'e3afed81-4a9c-4480-a78a-e0872408b95a'
client.cancel_transaction(transaction_id)
```

```javascript
var transactionId = 'e3afed81-4a9c-4480-a78a-e0872408b95a';
client.cancelTransaction(transactionId, function (err, msg) {
  console.log("cancel transaction err", err);
  console.log("cancel transaction", msg);
});
```

```php
<?php
$transactionId = 'e3afed81-4a9c-4480-a78a-e0872408b95a';
$client->cancelTransaction($transactionId);
?>
```

> The above command returns an HTTP response with status code 204

```ruby
# Hashie::Mash Object
response.status # 204
response.message # "This operation has completed successfully"
```

```python
# JSON Object
{ "status": 204, message: "This operation has completed successfully" }
```

```javascript
// JSON Object
{ status: 204, message: "This operation requires email confirmation" }
```

```php
<?php
// Array Object
[ "status" => 204, "message" => "This operation has completed successfully" ]
?>
```

Cancel a single transaction with the given ID.

### HTTP Request

`DELETE /v1/transactions/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the transaction to cancel



