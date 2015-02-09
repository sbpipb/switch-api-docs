# Products


## Get All Products

```shell
curl -X GET
     -H 'X-User-Email: warex03@gmail.com'
     -H 'X-User-Token: _KHS4euMs1At4jsUHHdR'
http://www.payswitch.net/api/products
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
http://www.payswitch.net/api/products/<id>
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