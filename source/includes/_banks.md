# Banks

Banks allow users to interact with bank accounts linked to their Buttercoin account

## Get all banks

```ruby
client.get_banks()
  ```

```python
client.get_banks()
```

```javascript
client.getBanks(function (err, banks) {
  console.log("banks err", err);
  console.log("banks", banks);
});
```

```php
<?php
$client->getBanks();
?>
```

```ruby
# Hashie::Mash Object
banks.each do |bank|
bank.bankId
end

```python
# Array of Dict Objects
[
  {
    "bankId": "54a89041680cd001r0a2dffe",
    "fullName": "Test User",
    "accountNumber": "*******89",
    "routingNumber": "*******21",
    "bankName": "USA Test Bank",
    "accountType": "CheckingAccount",
    "enabled": true,
    "verificationType": "InstantVerification",
    "verificationStatus": "Complete"
  }
]
```

```javascript
// JSON Array of Objects
[
  {
    "bankId": "54a89041680cd001r0a2dffe",
    "fullName": "Test User",
    "accountNumber": "*******89",
    "routingNumber": "*******21",
    "bankName": "USA Test Bank",
    "accountType": "CheckingAccount",
    "enabled": true,
    "verificationType": "InstantVerification",
    "verificationStatus": "Complete"
  }
]
```

```php
<?php
// Array of Array Objects
[
  [
    "bankId" => "54a89041680cd001r0a2dffe",
    "fullName" => "Test User",
    "accountNumber" => "*******89",
    "routingNumber" => "*******21",
    "bankName" => "USA Test Bank",
    "accountType" => "CheckingAccount",
    "enabled" => true,
    "verificationType" => "InstantVerification",
    "verificationStatus" => "Complete"
  ]
]
?>
```

This endpoint retrieves all banks for the current user

### HTTP Request

`GET /v1/banks`

## Get a single bank

```ruby
# Get bank with the ID
bank_id = '54a89041680cd001r0a2dffe'
client.get_bank_by_id(bank_id)

# For convenience, you can also get bank by full URL
url = 'https://api.buttercoin.com/v1/banks/54a89041680cd001r0a2dffe'
client.get_bank_by_url(url)
```

```python
# Get bank with the ID
bank_id = '54a89041680cd001r0a2dffe'
client.get_bank_by_id(bank_id)

# For convenience, you can also get bank by full URL
url = 'https://api.buttercoin.com/v1/banks/54a89041680cd001r0a2dffe'
client.get_bank_by_url(url)
```

```javascript
// Get bank with the ID
var bankId = '54a89041680cd001r0a2dffe';
client.getBankById(bankId, function (err, bank) {
  console.log("bank err", err);
  console.log("bank", bank);
});

// For convenience, you can also get bank by full URL
var url = 'https://api.buttercoin.com/v1/banks/54a89041680cd001r0a2dffe';
client.getBankByUrl(url, function (err, bank) {
  console.log("bank err", err);
  console.log("bank", bank);
});
```

```php
<?php
// Get bank with the ID
$bankId = '54a89041680cd001r0a2dffe';
$client->getBankById($bankId);

// For convenience, you can also get bank by full URL
$url = 'https://api.buttercoin.com/v1/banks/54a89041680cd001r0a2dffe';
$client->getBankByUrl($url);
?>
```

```ruby
# Hashie::Mash Object
bank.bankId # "54a89041680cd001r0a2dffe"
bank.accountNumber # "*******89"
```

```python
# Dict Object
{
  "bankId": "54a89041680cd001r0a2dffe",
  "fullName": "Test User",
  "accountNumber": "*******89",
  "routingNumber": "*******21",
  "bankName": "USA Test Bank",
  "accountType": "CheckingAccount",
  "enabled": true,
  "verificationType": "InstantVerification",
  "verificationStatus": "Complete"
}
```

```javascript
// Json Object
{
  "bankId": "54a89041680cd001r0a2dffe",
  "fullName": "Test User",
  "accountNumber": "*******89",
  "routingNumber": "*******21",
  "bankName": "USA Test Bank",
  "accountType": "CheckingAccount",
  "enabled": true,
  "verificationType": "InstantVerification",
  "verificationStatus": "Complete"
}
```

```php
<?php
// Array Object
[
  "bankId" => "54a89041680cd001r0a2dffe",
  "fullName" => "Test User",
  "accountNumber" => "*******89",
  "routingNumber" => "*******21",
  "bankName" => "USA Test Bank",
  "accountType" => "CheckingAccount",
  "enabled" => true,
  "verificationType" => "InstantVerification",
  "verificationStatus" => "Complete"
]
?>
```

This endpoint retrieves a single bank with the given ID.

### HTTP Request

`GET /v1/banks/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the bank to retrieve


## Delete a bank

```ruby
bank_id = '54a89041680cd001r0a2dffe'
client.delete_bank(bank_id)
```

```python
bank_id = '54a89041680cd001r0a2dffe'
client.cancel_bank(bank_id)
```

```javascript
var bankId = '54a89041680cd001r0a2dffe';
client.deleteBank(bankId, function (err, msg) {
  console.log("delete bank err", err);
  console.log("delete bank", msg);
});
```

```php
<?php
$bankId = '54a89041680cd001r0a2dffe';
$client->cancelBank($bankId);
?>
```

> The above command returns an HTTP response with status code 204

```ruby
# Hashie::Mash Object
response.status # 204
response.message # "This operation has completed successfully"
```

```python
# Dict Object
{ "status": 204, message: "This operation has completed successfully" }
```

```javascript
// JSON Object
{ status: 204, message: "This operation has completed successfully" }
```

```php
<?php
// Array Object
[ "status" => 204, "message" => "This operation has completed successfully" ]
?>
```

Delete a single bank with the given ID.

### HTTP Request

`DELETE /v1/banks/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the bank to delete

### More about Deleting Banks

Deleting a bank will remove the bank from your account. If you try to create new transaction with a bank that has been deleted, the request will be denied, but removing a bank will not affect any active transactions that are already being processed or have already been completed.

