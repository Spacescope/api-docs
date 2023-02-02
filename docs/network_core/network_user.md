---
sidebar_position: 9
---

# Network User

Population information on the Filecoin Network’s various network users or participants.

### Client Count

#### Description

The number of storage clients on the Filecoin Network.

#### Request URL

```js
GET: /network_user/client_count
```

#### Request Parameters
| **Variable** | **Type** | **Description**                         | **Example** | **Default**                  |
| ------------ | -------- | --------------------------------------- | ----------- | ---------------------------- |
| start_date   | STRING   | Start date of the selected period (Optional). | 2022-07-01  | The most recent date that the API includes. |
| end_date     | STRING   | End date of the selected period (Optional).  | 2022-07-01  | The most recent date that the API includes. |

:::note

 The difference between end_date and start_date should be smaller than 90 days.

:::


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

url = "https://api.spacescope.io/v2/network_user/client_count?end_date=2022-07-01&start_date=2022-07-01"

payload={}
headers = {
  'authorization': 'Bearer ghp_xJtTSVcNRJINLWMmfDangcIFCjqPUNZenoVe'
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
  url := "https://api.spacescope.io/v2/network_user/client_count?end_date=2022-07-01&start_date=2022-07-01"
  method := "GET"
  client := &http.Client {
  }
  req, err := http.NewRequest(method, url, nil)
  if err != nil {
    fmt.Println(err)
    return
  }
  req.Header.Add("authorization", "Bearer ghp_xJtTSVcNRJINLWMmfDangcIFCjqPUNZenoVe")
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
  'url': 'https://api.spacescope.io/v2/network_user/client_count?end_date=2022-07-01&start_date=2022-07-01',
  'headers': {
    'authorization': 'Bearer ghp_xJtTSVcNRJINLWMmfDangcIFCjqPUNZenoVe'
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
curl --location --request GET 'https://api.spacescope.io/v2/network_user/client_count?end_date=2022-07-01&start_date=2022-07-01' \
--header 'authorization: Bearer ghp_xJtTSVcNRJINLWMmfDangcIFCjqPUNZenoVe'
```

</TabItem>
</Tabs>

</div>
</details>


#### Response Schema

| **Variable**                   | **Type** | **Description**                                                                                                                                    |
| ------------------------------ | -------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| stat_date           | DATE  | Refers to the date the data was recorded.  |
| total_client_count          | BIGINT  | Cumulative count of the storage clients that has had at least one deal.                                                                           |
| total_verified_client_count             | BIGINT  | Cumulative count of the storage clients that has had at least one verified deal.  |

#### Response Example

<details><summary>Response</summary>
<div>

```Json
{
   "request_id": "ba4422cc-734f-4d90-84ec-7ad0b3ef01e7#23703",
   "code": 0,
   "message": "success.",
   "data": [
       {
           "stat_date": "2022-12-13T00:00:00Z",
           "total_client_count": 2196,
           "total_verified_client_count": 1135
       }
   ]
}
```
</div>
</details>
<hr />


### Address Count

#### Description

The number of unique addresses that have interacted with the blockchain over time, classified by status and address balance.

#### Request URL

```js
GET: /network_user/address_count
```

#### Request Parameters
| **Variable** | **Type** | **Description**                         | **Example** | **Default**                  |
| ------------ | -------- | --------------------------------------- | ----------- | ---------------------------- |
| start_date   | STRING   | Start date of the selected period (Optional). | 2022-07-01  | The most recent date that the API includes. |
| end_date     | STRING   | End date of the selected period (Optional).  | 2022-07-01  | The most recent date that the API includes. |

:::note

 The difference between end_date and start_date should be smaller than 90 days.

:::

#### Request Examples

<details><summary>Code</summary>
<div>



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

url = "https://api.spacescope.io/v2/network_user/address_count?end_date=2022-07-01&start_date=2022-07-01"

payload={}
headers = {
  'authorization': 'Bearer ghp_xJtTSVcNRJINLWMmfDangcIFCjqPUNZenoVe'
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
  url := "https://api.spacescope.io/v2/network_user/address_count?end_date=2022-07-01&start_date=2022-07-01"
  method := "GET"
  client := &http.Client {
  }
  req, err := http.NewRequest(method, url, nil)
  if err != nil {
    fmt.Println(err)
    return
  }
  req.Header.Add("authorization", "Bearer ghp_xJtTSVcNRJINLWMmfDangcIFCjqPUNZenoVe")
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
  'url': 'https://api.spacescope.io/v2/network_user/address_count?end_date=2022-07-01&start_date=2022-07-01',
  'headers': {
    'authorization': 'Bearer ghp_xJtTSVcNRJINLWMmfDangcIFCjqPUNZenoVe'
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
curl --location --request GET 'https://api.spacescope.io/v2/network_user/address_count?end_date=2022-07-01&start_date=2022-07-01' \
--header 'authorization: Bearer ghp_xJtTSVcNRJINLWMmfDangcIFCjqPUNZenoVe'
```

</TabItem>
</Tabs>

</div>
</details>


#### Response Schema

| **Variable**                | **Type** | **Description**                                        |
| :-------------------------- | :------- | :----------------------------------------------------- |
| stat_date                   | DATE     | Refers to the date the data was recorded. |
| total_address_count        | BIGINT  | The number of unique addresses ever created on Filecoin.                       |
| active_address_count_daily          | BIGINT  | The number of unique addresses that has interacted with the Filecoin blockchain at least once in the past 24 hours.                      |
| active_address_count_weekly          | BIGINT  | The number of unique addresses that has interacted with the Filecoin blockchain at least once in the past 7 days.                         |
| active_address_count_monthly          | BIGINT  | The number of unique addresses that has interacted with the Filecoin blockchain at least once in the past 30 days.       |
| total_address_count_100           | BIGINT  | The number of unique addresses on Filecoin with token balance >100 FIL.                        |
| total_address_count_1000         | BIGINT  | The number of unique addresses on Filecoin with token balance >1,000 FIL (including addresses with token balance >100 FIL).             |
| total_address_count_10000 | BIGINT | The number of unique addresses on Filecoin with token balance >10,000 FIL (including addresses with token balance >1,000 FIL). |
| total_address_count_100000 | BIGINT | The number of unique addresses on Filecoin with token balance >100,000 FIL (including addresses with token balance >10,000 FIL). |
| total_address_count_1000000 | BIGINT | The number of unique addresses on Filecoin with token balance >1,000,000 FIL (including addresses with token balance >100,000 FIL). |

#### Response Example

<details><summary>Response</summary>
<div>

```Json
{
   "request_id": "ba4422cc-734f-4d90-84ec-7ad0b3ef01e7#23701",
   "code": 0,
   "message": "success.",
   "data": [
       {
           "stat_date": "2022-12-01T00:00:00Z",
           "total_address_count": 1981165,
           "total_address_count_100": 58352,
           "total_address_count_1000": 16556,
           "total_address_count_10000": 4539,
           "total_address_count_100000": 815,
           "total_address_count_1000000": 52,
           "active_address_count_daily": 8380,
           "active_address_count_weekly": 20952,
           "active_address_count_monthly": 56088
       }
   ]
}
```
</div>
</details>
