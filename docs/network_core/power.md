---
sidebar_position: 4
---

# Power

Power provides information on the Filecoin Network’s data storage capacity, storage service states, and storage onboarding status. 

### Network Storage Capacity 


#### Description

The Filecoin Network’s storage capacity, presented in Raw Byte (RB) and Quality-Adjusted (QA) Power.

#### Request URL

```js
GET: /power/network_storage_capacity
```

#### Request Parameters
| **Variable** | **Type** | **Description**                         | **Example** | **Default**                  |
| ------------ | -------- | --------------------------------------- | ----------- | ---------------------------- |
| start_date   | STRING   | Start date of the selected period (Optional). | 2022-07-01  | The most recent date that the API includes. |
| end_date     | STRING   | End date of the selected period (Optional).   | 2022-07-01  | The most recent date that the API includes. |

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

url = "https://api.spacescope.io/v2/power/network_storage_capacity?end_date=2022-07-01&start_date=2022-07-01"

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
  url := "https://api.spacescope.io/v2/power/network_storage_capacity?end_date=2022-07-01&start_date=2022-07-01"
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
  'url': 'https://api.spacescope.io/v2/power/network_storage_capacity?end_date=2022-07-01&start_date=2022-07-01',
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
curl --location --request GET 'https://api.spacescope.io/v2/power/network_storage_capacity?end_date=2022-07-01&start_date=2022-07-01' \
--header 'authorization: Bearer <--Please replace your API key here-->'
```

</TabItem>
</Tabs>

</div>
</details>


#### Response Schema

| **Variable**                   | **Type** | **Description**                                                                                                                                    |
| ------------------------------ | -------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| stat_date                      | DATE     | Refers to the date the data was recorded.                                                                                                         |
| total_qa_bytes_power           | NUMERIC  | This parameter measures the consensus power of stored data on the network and is equal to Raw Byte Power multiplied by the average Sector Quality Multiplier of the network. |
| total_raw_bytes_power          | NUMERIC  | This measurement is the total size of the network’s storage capacity (with no adjustment) in bytes.                                                                                      |
| baseline_power             | NUMERIC  | The baseline power targeted by the network in bytes.                                                                                           |

#### Response Example

<details><summary>Response</summary>
<div>

```Json
{
    "request_id": "4e14a4aa-2368-4029-a660-5a883c0c29f1#606",
    "code": 0,
    "message": "success.",
    "data": [
        {
            "stat_date": "2022-07-01T00:00:00Z",
            "total_qa_bytes_power": 20431876696867700000,
            "total_raw_bytes_power": 19307467099059780000,
            "baseline_power": 10430930206272310000
        }
    ]
}
```
</div>
</details>
<hr />

### Storage State 


#### Description

Storage state based on active, faulty, terminated or recovered sectors.


#### Request URL

```js
GET: /power/storage_state
```

#### Request Parameters
| **Variable** | **Type** | **Description**                         | **Example** | **Default**                  |
| ------------ | -------- | --------------------------------------- | ----------- | ---------------------------- |
| start_date   | STRING   | Start date of the selected period (Optional). | 2022-07-01  | The most recent date that the API includes. |
| end_date     | STRING   | End date of the selected period (Optional).   | 2022-07-01  | The most recent date that the API includes. |

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

url = "https://api.spacescope.io/v2/power/storage_state?end_date=2022-07-01&start_date=2022-07-01"

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
  url := "https://api.spacescope.io/v2/power/storage_state?end_date=2022-07-01&start_date=2022-07-01"
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
  'url': 'https://api.spacescope.io/v2/power/storage_state?end_date=2022-07-01&start_date=2022-07-01',
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
curl --location --request GET 'https://api.spacescope.io/v2/power/storage_state?end_date=2022-07-01&start_date=2022-07-01' \
--header 'authorization: Bearer <--Please replace your API key here-->'
```

</TabItem>
</Tabs>

</div>
</details>


#### Response Schema

| **Variable**             | **Type** | **Description**                                                                                           |
| ------------------------ | -------- | --------------------------------------------------------------------------------------------------------- |
| stat_date                | DATE     | Refers to the date the data was recorded.                                                                |
| active_fault_rbp             | NUMERIC  | The total raw bytes storage power in TiB of outstanding faulted sectors that are not recovered or terminated.               |
| avg_days_active_fault       | NUMERIC  | Average days that a sector fault remains active on the Filecoin Network during the past 24 hours.         |
| daily_new_fault_rbp                  | NUMERIC  | Daily new faulted sector raw bytes power in TiB.                                                                           |
| daily_new_recover_rbp                | NUMERIC  | Daily new recovered sector raw bytes power in TiB.                                                                      |
| daily_new_terminate_rbp                   | NUMERIC  | Daily new terminated sector raw bytes power in TiB.                                                                      |
| daily_new_active_terminate_rbp            | NUMERIC  | Daily raw bytes power in TiB of sectors that are terminated actively by SPs.                            |
| daily_new_passive_terminate_rbp            | NUMERIC  | Daily raw bytes power in TiB of sectors that are terminated passively after 42 days in fault.                            |
| daily_new_extend_rbp              | NUMERIC  | Daily raw bytes power in TiB of sectors that are extended.                      |
| daily_new_extend_qap          | NUMERIC  | Daily quality-adjusted power in TiB of Sectors that are extended. |

#### Response Example

<details><summary>Response</summary>
<div>

```Json
{
    "request_id": "3c9078ba-dd89-4b0b-84ce-4035964eac3b#616",
    "code": 0,
    "message": "success.",
    "data": [
        {
            "stat_date": "2022-07-01T00:00:00Z",
            "active_fault_rbp": 99965.5,
            "avg_days_active_fault": 4.88184400559016,
            "daily_new_fault_rbp": 61826.15625,
            "daily_new_recover_rbp": 52422.6875,
            "daily_new_terminate_rbp": 367.0625,
            "daily_new_active_terminate_rbp": 366.78125,
            "daily_new_passive_terminate_rbp": 0.28125,
            "daily_new_extend_rbp": 88150.21875,
            "daily_new_extend_qap": 88150.2489709872
        }
    ]
}
```
</div>
</details>
<hr />

### Daily Power Onboarding by Method


#### Description

Sectors onboarded onto the Filecoin Network based on PreCommit and ProveCommit states during the last 24 hours.


#### Request URL

```js
GET: /power/daily_power_onboarding_by_method
```

#### Request Parameters
| **Variable** | **Type** | **Description**                         | **Example** | **Default**                  |
| ------------ | -------- | --------------------------------------- | ----------- | ---------------------------- |
| start_date   | STRING   | Start date of the selected period (Optional). | 2022-07-01  | The most recent date that the API includes. |
| end_date     | STRING   | End date of the selected period (Optional).   | 2022-07-01  | The most recent date that the API includes. |

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

url = "https://api.spacescope.io/v2/power/daily_power_onboarding_by_method?end_date=2022-07-01&start_date=2022-07-01"

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
  url := "https://api.spacescope.io/v2/power/daily_power_onboarding_by_method?end_date=2022-07-01&start_date=2022-07-01"
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
  'url': 'https://api.spacescope.io/v2/power/daily_power_onboarding_by_method?end_date=2022-07-01&start_date=2022-07-01',
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
curl --location --request GET 'https://api.spacescope.io/v2/power/daily_power_onboarding_by_method?end_date=2022-07-01&start_date=2022-07-01' \
--header 'authorization: Bearer <--Please replace your API key here-->'
```

</TabItem>
</Tabs>

</div>
</details>


#### Response Schema

| **Variable**                 | **Type** | **Description**                                                                                      |
| ---------------------------- | -------- | ---------------------------------------------------------------------------------------------------- |
| stat_date                    | DATE     | Refers to the date the data was recorded.                                                           |
| pre_commit_sector_rbp       | NUMERIC  | Daily PreCommitSector raw bytes power in PiB through single commit method.                                                                   |
| pre_commit_sector_batch_size | NUMERIC  | Daily PreCommitSecorBatch raw bytes power in PiB through batch commit method.                                                             |
| prove_commit_sector_size     | NUMERIC  | Daily ProveCommit raw bytes power in PiB through single commit method.                                                                 |
| prove_commit_aggregate_size  | NUMERIC  | Daily ProveCommitAggregate raw bytes power in PiB through aggregation.                                                             |

#### Response Example

<details><summary>Response</summary>
<div>

```Json
{
    "request_id": "3c9078ba-dd89-4b0b-84ce-4035964eac3b#617",
    "code": 0,
    "message": "success.",
    "data": [
        {
            "stat_date": "2022-07-01T00:00:00Z",
            "pre_commit_sector_rbp": 22.8249816894531,
            "pre_commit_sector_batch_rbp": 2.02978515625,
            "prove_commit_sector_rbp": 20.540283203125,
            "prove_commit_sector_agg_rbp": 4.78314208984375
        }
    ]
}
```
</div>
</details>
<hr />

### Daily Power Onboarding by Sector Size


#### Description

Sectors onboarded onto the Filecoin Network based on sector size, during the last 24 hours.

#### Request URL

```js
GET: /power/daily_power_onboarding_by_sector_size
```

#### Request Parameters
| **Variable** | **Type** | **Description**                         | **Example** | **Default**                  |
| ------------ | -------- | --------------------------------------- | ----------- | ---------------------------- |
| start_date   | STRING   | Start date of the selected period (Optional). | 2022-07-01  | The most recent date that the API includes. |
| end_date     | STRING   | End date of the selected period (Optional).   | 2022-07-01  | The most recent date that the API includes. |

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

url = "https://api.spacescope.io/v2/power/daily_power_onboarding_by_sector_size?end_date=2022-07-01&start_date=2022-07-01"

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
  url := "https://api.spacescope.io/v2/power/daily_power_onboarding_by_sector_size?end_date=2022-07-01&start_date=2022-07-01"
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
  'url': 'https://api.spacescope.io/v2/power/daily_power_onboarding_by_sector_size?end_date=2022-07-01&start_date=2022-07-01',
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
curl --location --request GET 'https://api.spacescope.io/v2/power/daily_power_onboarding_by_sector_size?end_date=2022-07-01&start_date=2022-07-01' \
--header 'authorization: Bearer <--Please replace your API key here-->'
```

</TabItem>
</Tabs>

</div>
</details>


#### Response Schema

| **Variable**       | **Type** | **Description**                                            |
| ------------------ | -------- | ---------------------------------------------------------- |
| stat_date          | DATE     | Refers to the date the data was recorded.                 |
| commit_rbp_32gib       | NUMERIC  | ProveCommit sector(32GiB) raw bytes power in bytes.                   |
| commit_qap_32gib | NUMERIC  | ProveCommit sector(32GiB) quality-adjusted power in bytes. |
| commit_rbp_64gib           | NUMERIC  | ProveCommit sector(64GiB) raw bytes power in bytes.                   |
| commit_qap_64gib      | NUMERIC  | ProveCommit sector(64GiB) quality-adjusted power in bytes. |

#### Response Example

<details><summary>Response</summary>
<div>

```Json
{
    "request_id": "3c9078ba-dd89-4b0b-84ce-4035964eac3b#617",
    "code": 0,
    "message": "success.",
    "data": [
        {
            "stat_date": "2022-07-01T00:00:00Z",
            "commit_rbp_32gib": 22259131867987970,
            "commit_qap_32gib": 28819681517947016,
            "commit_rbp_64gib": 6252510310301696,
            "commit_qap_64gib": 6640928820106764,
        }
    ]
}
```
</div>
</details>
<hr />


### Sectors Scheduled Expiration

#### Description

Reports the sector sizes and pledges of sectors that have historically been extended, expired or terminated, as well as sectors that are projected to expire in the future.

#### Request URL

```js
GET: /power/sectors_schedule_expiration
```

#### Request Parameters
| **Variable** | **Type** | **Description**                         | **Example** | **Default**                  |
| ------------ | -------- | --------------------------------------- | ----------- | ---------------------------- |
| start_date   | STRING   | Start date of the selected period (Optional). | 2022-07-01  | The most recent date that the API includes. |
| end_date     | STRING   | End date of the selected period (Optional).   | 2022-07-01  | The earliest date that the API includes. |

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

url = "https://api.spacescope.io/v2/power/sectors_schedule_expiration"

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
  url := "https://api.spacescope.io/v2/power/sectors_schedule_expiration"
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
  'url': 'https://api.spacescope.io/v2/power/sectors_schedule_expiration',
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
curl --location --request GET 'https://api.spacescope.io/v2/power/sectors_schedule_expiration' \
--header 'authorization: Bearer <--Please replace your API key here-->'
```

</TabItem>
</Tabs>

</div>
</details>


#### Response Schema

| **Variable**       | **Type** | **Description**                                            |
| ------------------ | -------- | ---------------------------------------------------------- |
| interest_date          | DATE     | Refers to the date the data was recorded (including the future date where the result is predicted).                 |
| schedule_expire_bytes       | BIGINT  | The total raw byte power (in bytes) of sectors scheduled to expire on the date of interest.                    |
| schedule_expire_bytes_qap | DOUBLE  | The total quality adjusted power (in bytes) of sectors scheduled to expire on the date of interest.  |
| extended_bytes           | BIGINT  | The total raw byte power (in bytes) of sectors that have been extended.                   |
| extended_bytes_qap      | DOUBLE  | The total quality adjusted power (in bytes) of sectors that have been extended. |
| terminated_bytes | BIGINT | The total raw byte power (in bytes) of sectors that have been terminated. |
| terminated_bytes_qap | DOUBLE | The total quality adjusted power (in bytes) of sectors that have been terminated. |
| expired_bytes | BIGINT | The total raw byte power (in bytes) of sectors that have expired or will potentially expire. |
| expired_bytes_qap | DOUBLE | The total quality adjusted power (in bytes) of sectors that have expired or will potentially expire. |
| schedule_expire_pledge | NUMERIC | The total initial pledge of sectors that have been scheduled to expire. |
| extended_pledge | NUMERIC | The total initial pledge of sectors that have been extended. |
| terminated_pledge | NUMERIC | The total initial pledge of sectors that have been terminated. |
| expired_pledge | NUMERIC | The total initial pledge of sectors that have expired or will potentially expire. |

#### Response Example

<details><summary>Response</summary>
<div>

```Json
{
   "request_id": "b403b94c-f5b0-4d55-a41e-d8b3686456f1#473269",
   "code": 0,
   "message": "success.",
   "data": [
       {
           "interest_date": "2022-12-01T00:00:00Z",
           "schedule_expire_bytes": 59437949330128896,
           "schedule_expire_bytes_qap": 59438963742920600,
           "extended_bytes": 36174310510952448,
           "extended_bytes_qap": 36174310510952400,
           "terminated_bytes": 1286497323974656,
           "terminated_bytes_qap": 1286497323974660,
           "expired_bytes": 36174310510952448,
           "expired_bytes_qap": 36174310510952400,
           "schedule_expire_pledge": 351437.763991308,
           "extended_pledge": 204537.213040628,
           "terminated_pledge": 7762.35876705795,
           "expired_pledge": 144719.994261654
       }
   ]
}
```
</div>
</details>
