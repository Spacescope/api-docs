---
sidebar_position: 1
---
# Deal Status

The current status of each deal, also including the status of the sector that the deal is associated with during its lifetime.

#### Request URL

```js
GET: /deals/deal_snapshot
```

#### Request Parameters
(Please at least input 1 of 6 optional params: deal_id, piece_cid, client_id, client_address, provider_id, provider_address)

| **Variable** | **Type** | **Description**  | **Example** | **Default**                  |
| ------------ | -------- | ---------------- | ----------- | ---------------------------- |
| page_size     | BIGINT   | The number of items to be displayed on one page (Required).  | 10  | / |
| page | BIGINT | The number of displayed page (Optional). | 5 | 0 |
| deal_id | BIGINT | Selected deal_id (Optional). | 3408838 | Unique ID of the deal. |
| piece_cid | STRING | Selected piece_cid (Optional). | baga6ea4seaqgbmifhs63 cij4uup7v7ax3jysnkmnd5fe sg3uwucv7hep2pikebq | CID of a sector piece. A Piece is an object that represents a whole or part of a File. |
| client_id | STRING | Selected client_id (Optional). | f01020500 | Unique ID of the storage client. |
| client_address | STRING | Selected address of the client (Optional). | f1xnypvbq2f5xbz5u4gzr gdmpz6kak4bmnfk7i2vq | Address of the storage client proposing the deal. |
| provider_id | STRING | Selected provider_id (Optional). | f01675012 | Unique ID of the storage provider. |
| provider_address | STRING | Selected address of the provider (Optional). | f2che6a4udf6jofehho4 qr5olzckfgdzexvpgj2pi | Address of the storage provider providing the services. |



#### Request Examples

<details><summary>Code</summary>
<div>


import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

<Tabs
  groupId="language"
  defaultValue="Python"
  values={[
    { label: 'Python', value: 'Python' },
    { label: 'GO', value: 'GO' },
    { label: 'NodeJS', value: 'NodeJS' },
    { label: 'cURL', value: 'cURL' }
  ]
}>

<TabItem value="Python">

```python
import requests

url = "https://api.spacescope.io/v2/deals/deal_snapshot?deal_id=3408838&page_size=10"

payload={}
headers = {
  'authorization': 'Bearer <--Please replace your API key here-->'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)

```

</TabItem>

<TabItem value="GO">

```go
package main
import (
  "fmt"
  "net/http"
  "io/ioutil"
)
func main() {
  url := "https://api.spacescope.io/v2/deals/deal_snapshot?deal_id=3408838&page_size=10"
  method := "GET"
  client := &http.Client {
  }
  req, err := http.NewRequest(method, url, nil)
  if err != nil {
    fmt.Println(err)
    return
  }
  req.Header.Add("authorization", "Bearer <--Please replace your API key here-->")
  res, err := client.Do(req)
  if err != nil {
    fmt.Println(err)
    return
  }
  defer res.Body.Close()

  body, err := ioutil.ReadAll(res.Body)
  if err != nil {
    fmt.Println(err)
    return
  }
  fmt.Println(string(body))
}
```

</TabItem>

<TabItem value="NodeJS">

```js
var request = require('request');
var options = {
  'method': 'GET',
  'url': 'https://api.spacescope.io/v2/deals/deal_snapshot?deal_id=3408838&page_size=10',
  'headers': {
    'authorization': 'Bearer <--Please replace your API key here-->'
  }
};
request(options, function (error, response) {
  if (error) throw new Error(error);
  console.log(response.body);
});
```

</TabItem>
<TabItem value="cURL">

```curl
curl --location --request GET 'https://api.spacescope.io/v2/deals/deal_snapshot?deal_id=3408838&page_size=10' \
--header 'authorization: Bearer <--Please replace your API key here-->'
```

</TabItem>
</Tabs>

</div>
</details>


#### Response Schema

| **Variable**                   | **Type** | **Description**                                                                                                                                    |
| ------------------------------ | -------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| deal_id           | BIGINT  | Unique ID of the deal.  |
| provider_id          | STRING  | Unique ID of the storage provider.                                                                                        |
| provider_address             | STRING  | Address of the storage provider providing the services (value of “-” means the address is unknown). |
| sector_id | STRING | Numeric ID of the sector where the deal is. |
| is_verified | BOOLEAN | Whether or not the deal is with a verified provider. |
| client_id | STRING | Unique ID of the client. |
| client_address | STRING | Address of the client proposing the deal (value of “-” means the address is unknown). |
| piece_cid | STRING | CID of a sector piece. A Piece is an object that represents a whole or part of a File. |
| padded_piece_size | BIGINT | The piece size in bytes with padding. |
| unpadded_piece_size | BIGINT | The piece size in bytes without padding. |
| sector_size | BIGINT | The sector size in bytes used by this storage provider for the deal. |
| start_epoch | BIGINT | The epoch at which this deal will begin. |
| end_epoch | BIGINT | The epoch at which this deal will end. |
| start_timestamp | TIMESTAMP | The timestamp at which this deal will begin. |
| end_timestamp | TIMESTAMP | The timestamp at which this deal will end. |
| storage_price_per_epoch | STRING | The amount of FIL (in attoFIL) that will be transferred from the client to the storage provider every epoch this deal is active for. |
| provider_collateral | STRING | The amount of FIL (in attoFIL) the storage provider has pledged as collateral. |
| client_collateral | STRING | The amount of FIL (in attoFIL) the client has pledged as collateral. |
| activation_epoch | BIGINT | The epoch at which the sector is activated. |
| expiration_epoch | BIGINT | The epoch at which the sector is scheduled to expire. |
| is_first | BOOLEAN | Whether or not this deal is recorded on the chain for the first time. |
| termination_epoch | BIGINT | The epoch at which the sector is terminated (-1 if the deal is never terminated). |
| snap_epoch | BIGINT | The epoch at which the sector is snapped (-1 if the deal is never snapped). |
| last_faulted_epoch | BIGINT | The epoch at which the sector last faulted (-1 if the deal is never faulted). |
| last_recovered_epoch | BIGINT | The epoch at which a faulted sector last recovered (-1 if the deal is never recovered). |
| deal_status | STRING | Current status of the Deal: active/terminated/faulted/expired. |
| total_fault_num | BIGINT | Total number of faults for the sector associated with this deal. |
| total_fault_days | NUMERIC | Total fault duration (in days) for the sector associated with this deal. |
| record_timestamp | TIMESTAMP | The timestamp at which this record is updated. |

#### Response Example

<details><summary>Response</summary>
<div>

```Json
{
   "request_id": "46bd7a2e-cc8e-4001-8595-1c699dba7108#171350",
   "code": 0,
   "message": "success.",
   "data": [
       {
           "deal_id": 3408838,
           "provider_id": "f01675012",
           "provider_address": "f2che6a4udf6jofehho4qr5olzckfgdzexvpgj2pi",
           "sector_id": "2349",
           "is_verified": true,
           "client_id": "f01020500",
           "client_address": "f1xnypvbq2f5xbz5u4gzrgdmpz6kak4bmnfk7i2vq",
           "piece_cid": "baga6ea4seaqgbmifhs63cij4uup7v7ax3jysnkmnd5fesg3uwucv7hep2pikebq",
           "padded_piece_size": 34359738368,
           "unpadded_piece_size": 34091302912,
           "sector_size": 34359738368,
           "start_epoch": 1482707,
           "end_epoch": 3023507,
           "start_timestamp": "2022-01-21T17:53:30Z",
           "end_timestamp": "2023-07-10T17:53:30Z",
           "storage_price_per_epoch": "0",
           "provider_collateral": "5041200106022921",
           "client_collateral": "0",
           "activation_epoch": 1469095,
           "expiration_epoch": 3023507,
           "is_first": false,
           "termination_epoch": -1,
           "snap_epoch": -1,
           "last_faulted_epoch": -1,
           "last_recovered_epoch": -1,
           "deal_status": "active",
           "total_fault_num": 0,
           "total_fault_days": 0,
           "record_timestamp": "2022-11-23T06:11:46.614Z"
       }
   ]
}
```
</div>
</details>
