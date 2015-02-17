# Transactions


## Get All Transactions

```shell
curl -X GET
     -H 'X-User-Email: warex03@gmail.com'
     -H 'X-User-Token: _KHS4euMs1At4jsUHHdR'
     -F "per_page=2"
     -F "page=1"
     -F "prod_cat_id=5"
     -F "date_from=2/2/15"
     -F "date_to=2/4/15"
http://www.payswitch.net/transactions
```

```ruby
require 'net/https'

uri = URI("http://www.payswitch.net/transactions")
params = {
  per_page: 2,
  page: 1,
  prod_cat_id: 5,
  date_from: '2/2/15',
  date_to: '2/4/15'
}
uri.query = URI.encode_www_form(params)

http = Net::HTTP.new(uri.host, uri.port)
request_uri = Net::HTTP::Get.new(uri.request_uri)
request_uri.add_field('X-User-Email', 'warex03@gmail.com')
request_uri.add_field('X-User-Token', '_KHS4euMs1At4jsUHHdR')

response = http.request(request_uri)
body = response.body
```

```python
import urllib
import urllib2

URL = "http://www.payswitch.net/transactions"
HEADERS = {
    'X-User-Email' : 'warex03@gmail.com',
    'X-User-Token' : '_KHS4euMs1At4jsUHHdR'
}
PARAMS = {
    'per_page' : 2,
    'page' : 1,
    'prod_cat_id' : 5,
    'date_from' : '2/2/15',
    'date_to' : '2/4/15',
}
QUERY_PARAMS = urllib.urlencode(PARAMS)
URL = URL + '?' + QUERY_PARAMS

request = urllib2.Request(URL, headers=HEADERS)
response = urllib2.urlopen(request).read()
```

> The JSON return value looks like this:

```json
{
    "num_pages": 20,
    "transactions": [
        {
            "id": 1213,
            "payload": {
                "account_id": "09294358409"
            },
            "cost": "15.0",
            "created_at": "2015-02-16T14:12:54.000+08:00",
            "provider_refno": "089041145634",
            "provider_message": {
                "code": null,
                "message": "Transaction successful."
            },
            "transaction_status": {
                "code": "00",
                "name": "Successful",
                "description": "Transaction has been successful"
            },
            "user": {
                "id": 2,
                "type": "Branch",
                "name": "Demo Branch",
                "merchant": {
                    "id": 1,
                    "name": "Demo Merchant"
                }
            },
            "provider_product": {
                "id": 110,
                "product_category_root_id": 1,
                "product": {
                    "id": 110,
                    "name": "Smart 15"
                },
                "provider": {
                    "id": 1,
                    "name": "OksPinoy"
                }
            }
        },
        {
            "id": 1212,
            "payload": {
                "account_id": "09278875368"
            },
            "cost": "15.0",
            "created_at": "2015-02-13T18:46:43.000+08:00",
            "provider_refno": "1693312999",
            "provider_message": {
                "code": null,
                "message": "Transaction successful."
            },
            "transaction_status": {
                "code": "00",
                "name": "Successful",
                "description": "Transaction has been successful"
            },
            "user": {
                "id": 8,
                "type": "BranchAgent",
                "name": "Demo 2 Payswitch",
                "merchant": {
                    "id": 1,
                    "name": "Demo Merchant"
                }
            },
            "provider_product": {
                "id": 317,
                "product_category_root_id": 1,
                "product": {
                    "id": 336,
                    "name": "Globe 15"
                },
                "provider": {
                    "id": 11,
                    "name": "EcpayLoad"
                }
            }
        }
    ]
}
```

Get all successful transactions of the user and all its branches/agents.

### HTTP Request

`GET http://www.payswitch.net/transactions`

### Query Parameters

Parameter | Type | Description
--------- | ---- | -----------
per_page | numeric<br/>(optional) | Number of items per page
page | numeric<br/>(optional) | Page number. Must be present together with per_page.
prod_cat_id | numeric<br/>(optional) | Get only transactions with this prod_cat_id
date_from | date<br/>(optional) | Get transactions starting from this date. Must be present together with date_to. Format: mm/dd/yy.
date_to | date<br/>(optional) | Get transactions until this date. Must be present together with date_from. Format: mm/dd/yy.

### Header Parameters

Parameter | Type | Description
--------- | ------- | -----------
X-User-Email | string<br/>(required) | The user's email address
X-User-Token | string<br/>(required) | The user's authentication token


## Get a Specific Transaction

```shell
curl -X GET
     -H 'X-User-Email: warex03@gmail.com'
     -H 'X-User-Token: _KHS4euMs1At4jsUHHdR'
http://www.payswitch.net/transactions/<id>
```

```ruby
require 'net/https'

uri = URI("http://www.payswitch.net/transactions/<id>")
http = Net::HTTP.new(uri.host, uri.port)
request_uri = Net::HTTP::Get.new(uri.request_uri)
request_uri.add_field('X-User-Email', 'warex03@gmail.com')
request_uri.add_field('X-User-Token', '_KHS4euMs1At4jsUHHdR')

response = http.request(request_uri)
body = response.body
```

```python
import urllib2

URL = "http://www.payswitch.net/transactions/<id>"
HEADERS = {
    'X-User-Email' : 'warex03@gmail.com',
    'X-User-Token' : '_KHS4euMs1At4jsUHHdR'
}

request = urllib2.Request(URL, headers=HEADERS)
response = urllib2.urlopen(request).read()
```

> The JSON return value looks like this:

```json
{
    "id": 1216,
    "payload": {
        "account_id": "4"
    },
    "cost": "15.0",
    "created_at": "2015-02-17T16:14:56.000+08:00",
    "provider_refno": null,
    "provider_message": {
        "code": "3000",
        "message": "MOBILE NUMBER IS INVALID"
    },
    "transaction_status": {
        "code": "08",
        "name": "Invalid cost / amount entered",
        "description": "You have entered an invalid cost / amount for the payload"
    },
    "user": {
        "id": 2,
        "type": "Branch",
        "name": "Demo Branch",
        "merchant": {
            "id": 1,
            "name": "Demo Merchant"
        }
    },
    "provider_product": {
        "id": 502,
        "product_category_root_id": 1,
        "product": {
            "id": 336,
            "name": "Globe 15"
        },
        "provider": {
            "id": 3,
            "name": "Ayannah"
        }
    }
}
```

Get the details of a specific transaction by using transaction id.

### HTTP Request

`GET http://www.payswitch.net/transactions/<id>`

### Header Parameters

Parameter | Type | Description
--------- | ------- | -----------
X-User-Email | string<br/>(required) | The user's email address
X-User-Token | string<br/>(required) | The user's authentication token


## Create an E-load Transaction using SKU

```shell
curl -X POST
     -H 'X-User-Email: warex03@gmail.com'
     -H 'X-User-Token: _KHS4euMs1At4jsUHHdR'
     -F "sku=GLOBE15"
     -F "payload[account_id]=09273031099"
http://www.payswitch.net/transactions
```

```ruby
require 'net/https'

uri = URI("http://www.payswitch.net/transactions")
params = {
  "sku" => "GLOBE15",
  "payload[account_id]" => "09273031099"
}
http = Net::HTTP.new(uri.host, uri.port)
request_uri = Net::HTTP::Post.new(uri.request_uri)
request_uri.add_field('X-User-Email', 'warex03@gmail.com')
request_uri.add_field('X-User-Token', '_KHS4euMs1At4jsUHHdR')
request_uri.set_form_data(params)

response = http.request(request_uri)
body = response.body
```

```python
import urllib
import urllib2

URL = "http://www.payswitch.net/transactions"
HEADERS = {
    'X-User-Email' : 'warex03@gmail.com',
    'X-User-Token' : '_KHS4euMs1At4jsUHHdR'
}
PARAMS = {
    'sku' : 'GLOBE15',
    'payload[account_id]' : '09273031099'
}

data = urllib.urlencode(values)
request = urllib2.Request(URL, data=data, headers=HEADERS)
response = urllib2.urlopen(request).read()
```

> The JSON return value looks like this:

```json
{
  "id": 11284,
  "payload": {
    "account_id": "09273031093"
  },
  "cost": "15.0",
  "created_at": "2015-02-05T23:16:35.196+08:00",
  "provider_refno": "1634974470",
  "transaction_status": {
    "code": "00",
    "name": "Successful",
    "description": "Transaction has been successful"
  },
  "user": {
    "id": 2,
    "type": "Branch",
    "name": "Demo Branch",
    "merchant": {
      "id": 1,
      "name": "Demo Merchant"
    }
  },
  "provider_product": {
    "id": 1,
    "product_category_root_id": 1,
    "product": {
      "id": 336,
      "sku": "GLOBE15",
      "name": "Globe 15"
    },
    "provider": {
      "id": 11,
      "name": "EcpayLoad"
    }
  }
}
```

Create a transaction by passing the sku and mobile number as payload.

### HTTP Request

`POST http://www.payswitch.net/transactions`

### Transaction Payloads

Parameter | Type | Description
--------- | ---- | -----------
sku | string<br/>(required) | The product's SKU code
payload[account_id] | string<br/>(required) | The mobile number of the customer

### Header Parameters

Parameter | Type | Description
--------- | ---- | -----------
X-User-Email | string<br/>(required) | The user's email address
X-User-Token | string<br/>(required) | The user's authentication token


## Create an E-load Transaction using Product ID

```shell
curl -X POST
     -H 'X-User-Email: warex03@gmail.com'
     -H 'X-User-Token: _KHS4euMs1At4jsUHHdR'
     -F "product_id=336"
     -F "payload[account_id]=09273031099"
http://www.payswitch.net/transactions
```

```ruby
require 'net/https'

uri = URI("http://www.payswitch.net/transactions")
params = {
  "product_id" => 336,
  "payload[account_id]" => "09273031099"
}
http = Net::HTTP.new(uri.host, uri.port)
request_uri = Net::HTTP::Post.new(uri.request_uri)
request_uri.add_field('X-User-Email', 'warex03@gmail.com')
request_uri.add_field('X-User-Token', '_KHS4euMs1At4jsUHHdR')
request_uri.set_form_data(params)

response = http.request(request_uri)
body = response.body
```

```python
import urllib
import urllib2

URL = "http://www.payswitch.net/transactions"
HEADERS = {
    'X-User-Email' : 'warex03@gmail.com',
    'X-User-Token' : '_KHS4euMs1At4jsUHHdR'
}
PARAMS = {
    'product_id' : 336,
    'payload[account_id]' : '09273031099'
}

data = urllib.urlencode(values)
request = urllib2.Request(URL, data=data, headers=HEADERS)
response = urllib2.urlopen(request).read()
```

> The JSON return value looks like this:

```json
{
  "id": 11284,
  "payload": {
    "account_id": "09273031093"
  },
  "cost": "15.0",
  "created_at": "2015-02-05T23:16:35.196+08:00",
  "provider_refno": "1634974470",
  "transaction_status": {
    "code": "00",
    "name": "Successful",
    "description": "Transaction has been successful"
  },
  "user": {
    "id": 2,
    "type": "Branch",
    "name": "Demo Branch",
    "merchant": {
      "id": 1,
      "name": "Demo Merchant"
    }
  },
  "provider_product": {
    "id": 1,
    "product_category_root_id": 1,
    "product": {
      "id": 336,
      "sku": "GLOBE15",
      "name": "Globe 15"
    },
    "provider": {
      "id": 11,
      "name": "EcpayLoad"
    }
  }
}
```

Create a transaction by passing the product id and mobile number as payload.

### HTTP Request

`POST http://www.payswitch.net/transactions`

### Transaction Payloads

Parameter | Type | Description
--------- | ---- | -----------
product_id | numeric<br/>(required) | The product's id
payload[account_id] | string<br/>(required) | The mobile number of the customer

### Header Parameters

Parameter | Type | Description
--------- | ---- | -----------
X-User-Email | string<br/>(required) | The user's email address
X-User-Token | string<br/>(required) | The user's authentication token