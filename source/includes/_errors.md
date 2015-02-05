# Status Codes

The Payswitch API uses the following status codes:


Status Code | Name | Description
----------- | ---- | -----------
00 | Successful | Transaction has been successful
01 | Insufficient balance | Transaction hasn't been successful due to insufficient credits
02 | Service providers are down | Transaction wasn't fulfilled because all providers are unavailable
03 | Invalid API Key | You are not authorized to create this transaction
04 | System error | Internal service error
05 | Invalid account id | The account you entered
06 | Invalid product code | The service you're trying to access doesn't exist
07 | Invalid payload for the SKU | The API payload needed to fulfill the transaction is incorrect, or insufficient
08 | Invalid cost / amount entered | You have entered an invalid cost / amount for the payload
09 | Not found | Service not found
10 | Failed to complete transaction | Incomplete transaction
11 | Client correlator already used | Client correlator entered is a duplicate