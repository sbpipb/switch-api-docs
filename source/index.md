---
title: Payswitch API Reference

language_tabs:
  - shell
  - ruby
  - python

toc_footers:
  - <a href='http://www.payswitch.net'>Sign Up for a Developer Key</a>
  - <a href='http://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to Payswitch API Documentation! You can use our API to access Payswitch API endpoints, which allows you to connect to our platform's services and start creating your own app.

We have language bindings in Shell, Ruby, and Python! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.




# Register User

To use the API, you need to sign up first at [www.payswitch.net](http://www.payswitch.net) so we can make your account and give your credentials (email address and auth token).



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
  "num_pages": 197,
  "transactions": [
    {
      "id": 1104,
      "payload": {
        "field1": "123",
        "field2": "123"
      },
      "cost": "1.0",
      "created_at": "2015-01-21T13:09:16.000+08:00",
      "provider_refno": null,
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
        "id": 196,
        "product_category_root_id": 15,
        "product": {
          "id": 205,
          "name": "SSS - Voluntary Member"
        },
        "provider": {
          "id": 5,
          "name": "Gcash Bancnet"
        }
      }
    },
    {
      "id": 1103,
      "payload": {
        "field1": "1231232",
        "field2": "123"
      },
      "cost": "330.0",
      "created_at": "2015-01-21T12:59:05.000+08:00",
      "provider_refno": null,
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
        "id": 196,
        "product_category_root_id": 15,
        "product": {
          "id": 205,
          "name": "SSS - Voluntary Member"
        },
        "provider": {
          "id": 5,
          "name": "Gcash Bancnet"
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
  "id": 1095,
  "payload": {
    "account_id": "123"
  },
  "cost": "10.0",
  "created_at": "2015-01-20T18:46:51.000+08:00",
  "provider_refno": null,
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
      "id": 1,
      "name": "Sun 10"
    },
    "provider": {
      "id": 2,
      "name": "Xpressload"
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




# Product Categories


## Get Main Product Categories

```shell
curl -X GET
     -H 'X-User-Email: warex03@gmail.com'
     -H 'X-User-Token: _KHS4euMs1At4jsUHHdR'
http://www.payswitch.net/api/product_categories/main
```

```ruby
require 'net/https'

URL = "http://www.payswitch.net/api/product_categories/main"

uri = URI.parse(URL)
http = Net::HTTP.new(uri.host, uri.port)
request_uri = Net::HTTP::Get.new(uri.request_uri)
request_uri.add_field('X-User-Email', 'warex03@gmail.com')
request_uri.add_field('X-User-Token', '_KHS4euMs1At4jsUHHdR')
response = http.request(request_uri)
body = response.body
```

```python
import urllib2

URL = "http://www.payswitch.net/api/product_categories/main"
HEADERS = {
    'X-User-Email' : 'warex03@gmail.com',
    'X-User-Token' : '_KHS4euMs1At4jsUHHdR'
}
request = urllib2.Request(URL, headers=HEADERS)
response = urllib2.urlopen(request).read()
```

> The JSON return value looks like this:

```json
[
    {
        "id": 1,
        "name": "E-load",
        "created_at": "2014-09-10T13:32:56.000+08:00"
    },
    {
        "id": 5,
        "name": "Gaming Pins",
        "created_at": "2014-09-10T13:32:56.000+08:00"
    },
    {
        "id": 12,
        "name": "Mobile Money",
        "created_at": "2014-09-10T13:32:56.000+08:00"
    },
    {
        "id": 15,
        "name": "Bills Payment",
        "created_at": "2014-09-10T13:32:56.000+08:00"
    },
    {
        "id": 28,
        "name": "Travel",
        "created_at": "2014-09-10T13:32:56.000+08:00"
    },
    {
        "id": 29,
        "name": "Microinsurance",
        "created_at": "2014-09-10T13:32:56.000+08:00"
    }
]
```

Get the main product categories.

### HTTP Request

`GET http://www.payswitch.net/api/product_categories/main`

### Header Parameters

Parameter | Type | Description
--------- | ------- | -----------
X-User-Email | string<br/>(required) | The user's email address
X-User-Token | string<br/>(required) | The user's authentication token


## Get Product Categories with Product Listing

```shell
curl -X GET
     -H 'X-User-Email: warex03@gmail.com'
     -H 'X-User-Token: _KHS4euMs1At4jsUHHdR'
http://www.payswitch.net/api/product_categories/<id>
```

```ruby
require 'net/https'

URL = "http://www.payswitch.net/api/product_categories/<id>"

uri = URI.parse(URL)
http = Net::HTTP.new(uri.host, uri.port)
request_uri = Net::HTTP::Get.new(uri.request_uri)
request_uri.add_field('X-User-Email', 'warex03@gmail.com')
request_uri.add_field('X-User-Token', '_KHS4euMs1At4jsUHHdR')
response = http.request(request_uri)
body = response.body
```

```python
import urllib2

URL = "http://www.payswitch.net/api/product_categories/<id>"
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
  "id": 6,
  "name": "E-Games",
  "description": null,
  "position": null,
  "products": [
    {
      "id": 127,
      "name": "E-games 10 points",
      "description": "E-games 10 points",
      "payload": {
        "account_id": "string"
      }
    },
    {
      "id": 128,
      "name": "E-games 100 points",
      "description": "E-games 100 points",
      "payload": {
        "account_id": "string"
      }
    },
    {
      "id": 129,
      "name": "E-games 1000 points",
      "description": "E-games 1000 points",
      "payload": {
        "account_id": "string"
      }
    }
  ],
  "children": []
}
```

Get the product categories containing the list of their products (if available).

### HTTP Request

`GET http://www.payswitch.net/api/product_categories/<id>`

### Header Parameters

Parameter | Type | Description
--------- | ------- | -----------
X-User-Email | string<br/>(required) | The user's email address
X-User-Token | string<br/>(required) | The user's authentication token




# Products


## Get All Products

```shell
curl -X GET
     -H 'X-User-Email: warex03@gmail.com'
     -H 'X-User-Token: _KHS4euMs1At4jsUHHdR'
http://www.payswitch.net/api/products"
```

```ruby
require 'net/https'

URL = "http://www.payswitch.net/api/products"

uri = URI.parse(URL)
http = Net::HTTP.new(uri.host, uri.port)
request_uri = Net::HTTP::Get.new(uri.request_uri)
request_uri.add_field('X-User-Email', 'warex03@gmail.com')
request_uri.add_field('X-User-Token', '_KHS4euMs1At4jsUHHdR')
response = http.request(request_uri)
body = response.body
```

```python
import urllib2

URL = "http://www.payswitch.net/api/products"
HEADERS = {
    'X-User-Email' : 'warex03@gmail.com',
    'X-User-Token' : '_KHS4euMs1At4jsUHHdR'
}
request = urllib2.Request(URL, headers=HEADERS)
response = urllib2.urlopen(request).read()
```

> The JSON return value looks like this:

```json
[
  {
    "id": 1,
    "product_category_id": 4,
    "name": "Sun 10"
  },
  {
    "id": 2,
    "product_category_id": 4,
    "name": "Sun 50"
  },
  {
    "id": 3,
    "product_category_id": 4,
    "name": "Sun 150"
  },
  {
    "id": 4,
    "product_category_id": 4,
    "name": "Sun 300"
  },
  {
    "id": 5,
    "product_category_id": 4,
    "name": "Sun 500"
  }
]
```

Get the list of all products.

### HTTP Request

`GET http://www.payswitch.net/api/products`

### Header Parameters

Parameter | Type | Description
--------- | ------- | -----------
X-User-Email | string<br/>(required) | The user's email address
X-User-Token | string<br/>(required) | The user's authentication token


## Get Product Details

```shell
curl -X GET
     -H 'X-User-Email: warex03@gmail.com'
     -H 'X-User-Token: _KHS4euMs1At4jsUHHdR'
http://www.payswitch.net/api/products/<id>"
```

```ruby
require 'net/https'

URL = "http://www.payswitch.net/api/products/<id>"

uri = URI.parse(URL)
http = Net::HTTP.new(uri.host, uri.port)
request_uri = Net::HTTP::Get.new(uri.request_uri)
request_uri.add_field('X-User-Email', 'warex03@gmail.com')
request_uri.add_field('X-User-Token', '_KHS4euMs1At4jsUHHdR')
response = http.request(request_uri)
body = response.body
```

```python
import urllib2

URL = "http://www.payswitch.net/api/products/<id>"
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
  "id": 55,
  "product_category_id": 2,
  "sku": "GLOBEUnlitxt20",
  "name": "Globe Unlitxt20",
  "credits": "20.0",
  "enabled": false,
  "created_at": "2014-09-10T13:33:01.000+08:00",
  "description": "Globe Promos",
  "payload": {
    "account_id": "string"
  }
}
```

Get the details of a product given its id.

### HTTP Request

`GET http://www.payswitch.net/api/products/<id>`

### Header Parameters

Parameter | Type | Description
--------- | ------- | -----------
X-User-Email | string<br/>(required) | The user's email address
X-User-Token | string<br/>(required) | The user's authentication token