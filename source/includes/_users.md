# User

## Get Current User Details

```shell
curl -X GET
     -H 'X-User-Email: warex03@gmail.com'
     -H 'X-User-Token: _KHS4euMs1At4jsUHHdR'
http://www.payswitch.net/api/users
```

```ruby
require 'net/https'

uri = URI("http://www.payswitch.net/api/users")

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

URL = "http://www.payswitch.net/api/users"
HEADERS = {
    'X-User-Email' : 'warex03@gmail.com',
    'X-User-Token' : '_KHS4euMs1At4jsUHHdR'
}

request = urllib2.Request(URL, headers=HEADERS)
response = urllib2.urlopen(request).read()
```
> JSON output

```json
{
    "info": "Current User",
    "user": {
        "id": 2,
        "email": "branch@demomerchant.com",
        "created_at": "2014-09-10T13:32:58.000+08:00",
        "updated_at": "2015-03-31T13:08:15.000+08:00",
        "merchant_id": 1,
        "branch_id": null,
        "name": "Demo Branch",
        "authentication_token": "_KHS4euMs1At4jsUHHdR",
        "plutus_account_id": 7,
        "contact_number": null,
        "banned": false,
        "plan_id": null
    },
    "user_type": "Branch",
    "balance": "680.00"
}	
```
Get the details of the current user

### HTTP Request

`GET http://www.payswitch.net/api/users`

### Header Parameters

Parameter | Type | Description
--------- | ------- | -----------
X-User-Email | string<br/>(required) | The user's email address
X-User-Token | string<br/>(required) | The user's authentication token