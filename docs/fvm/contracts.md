---
sidebar_position: 6
---

# Contracts

Contracts provides information on contract deployment statistics on Filecoin Virtual Machine, including 
counts of contracts, users and transactions.

### Contracts Deployed

#### Description

The daily number of unique contracts deployed on FEVM.

#### Request URL

```js
GET: /v2/fvm/contracts_deployed
```

#### Request Parameters
| **Variable** | **Type** | **Description**                         | **Example** | **Default**                  |
| ------------ | -------- | --------------------------------------- | ----------- | ---------------------------- |
| start_date   | STRING   | Start date of the selected period (Optional). | 2022-07-01  | The most recent date that the API includes. |
| end_date     | STRING   | End date of the selected period (Optional).   | 2022-07-01  | The most recent date that the API includes. |

:::note

 When no dates are specified, all available historical data is returned. 

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

url = "https://api.spacescope.io/v2/fvm/contracts_deployed?end_date=2023-03-16&start_date=2023-03-01"

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
  url := "https://api.spacescope.io/v2/fvm/contracts_deployed?end_date=2023-03-16&start_date=2023-03-01"
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
  'url': 'https://api.spacescope.io/v2/fvm/contracts_deployed?end_date=2023-03-16&start_date=2023-03-01',
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
curl --location --request GET 'https://api.spacescope.io/v2/fvm/contracts_deployed?end_date=2023-03-16&start_date=2023-03-01' \
--header 'authorization: Bearer <--Please replace your API key here-->'
```

</TabItem>
</Tabs>

</div>
</details>


#### Response Schema

| **Variable**             | **Type** | **Description**                                                              |
|--------------------------|----------|------------------------------------------------------------------------------|
| stat_date                | DATE     | Date, in YYYY-MM-DD.                                                         |
| new_contract_count_daily | BIGINT   | Number of new unique contracts recorded on chain each day.                   |
| total_contract_count     | BIGINT   | The cumulative number of new unique contracts recorded on chain on each day. |
| total_deployer_address_count | BIGINT | The cumulative number of unique deployer addresses as of specified day.    | 

#### Response Example

<details><summary>Response</summary>
<div>

```Json

{
  "request_id":"d1b19b0f-ed01-4275-89a5-31d57f4e0ea8#56176",
  "code":0,
  "message":"success.",
  "data": [
    {
      "stat_date":"2023-03-14T00:00:00Z",
      "new_contract_count_daily":76,
      "total_contract_count":76
      }
  ]
}

```
</div>
</details>
<hr />

### Transaction Counts 

#### Description

The daily number of contract interactions across all contracts in FEVM. 

#### Request URL

```js
GET: /v2/fvm/contract_interactions

```

#### Request Parameters
| **Variable** | **Type** | **Description**                         | **Example** | **Default**                  |
| ------------ | -------- | --------------------------------------- | ----------- | ---------------------------- |
| start_date   | STRING   | Start date of the selected period (Optional). | 2022-07-01  | The most recent date that the API includes. |
| end_date     | STRING   | End date of the selected period (Optional).   | 2022-07-01  | The most recent date that the API includes. |

:::note

 When no dates are specified, all available historical data is returned. 

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

url = "https://api.spacescope.io/v2/fvm/contract_interactions?end_date=2023-03-16&start_date=2023-03-01"

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
  url := "https://api.spacescope.io/v2/fvm/contract_interactions?end_date=2023-03-16&start_date=2023-03-01"
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
  'url': 'https://api.spacescope.io/v2/fvm/contract_interactions?end_date=2023-03-16&start_date=2023-03-01',
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
curl --location --request GET 'https://api.spacescope.io/v2/fvm/contract_interactions?end_date=2023-03-16&start_date=2023-03-01' \
--header 'authorization: Bearer <--Please replace your API key here-->'
```

</TabItem>
</Tabs>

</div>
</details>


#### Response Schema

| **Variable**             | **Type** | **Description**                                                                                                                    |
|--------------------------|----------|------------------------------------------------------------------------------------------------------------------------------------|
| stat_date                | DATE     | Date, in YYYY-MM-DD.                                                                                                               |
| total_internal_txn_count | BIGINT   | The number of internal transactions per day. Internal transactions are transactions occurring between smart contracts.             |
| total_external_txn_count | BIGINT   | The number of contract transactions per day. Transactions, also known as external transactions, occur between external addresses.  |
                                  |

#### Response Example

<details><summary>Response</summary>
<div>

```Json
{
    "request_id": "d1b19b0f-ed01-4275-89a5-31d57f4e0ea8#56253",
    "code": 0,
    "message": "success.",
    "data": [
        {
            "stat_date": "2023-03-16T00:00:00Z",
            "total_internal_txn_count": 735,
            "total_external_txn_count": 18735,
            "total_txn_count": 19470
        }
    ]
}
```
</div>
</details>
<hr />



<!-- Active contract users -->
### Active Contract Users

#### Description

The daily number of unique active contract users in the FEVM.

#### Request URL

```js
GET: /v2/fvm/active_contract_users

```

#### Request Parameters
| **Variable** | **Type** | **Description**                         | **Example** | **Default**                  |
| ------------ | -------- | --------------------------------------- | ----------- | ---------------------------- |
| start_date   | STRING   | Start date of the selected period (Optional). | 2022-07-01  | The most recent date that the API includes. |
| end_date     | STRING   | End date of the selected period (Optional).   | 2022-07-01  | The most recent date that the API includes. |

:::note

 When no dates are specified, all available historical data is returned. 

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

url = "https://api.spacescope.io/v2/fvm/active_contract_users?end_date=2023-03-16&start_date=2023-03-01"

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
  url := "https://api.spacescope.io/v2/fvm/active_contract_users?end_date=2023-03-16&start_date=2023-03-01"
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
  'url': 'https://api.spacescope.io/v2/fvm/active_contract_users?end_date=2023-03-16&start_date=2023-03-01',
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
curl --location --request GET 'https://api.spacescope.io/v2/fvm/active_contract_users?end_date=2023-03-16&start_date=2023-03-01' \
--header 'authorization: Bearer <--Please replace your API key here-->'
```

</TabItem>
</Tabs>

</div>
</details>


#### Response Schema

| **Variable**            | **Type** | **Description**                                                                                                                                                                  |
|-------------------------|----------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| stat_date               | DATE     | Date, in YYYY-MM-DD.                                                                                                                                                             |
| active_user_count_daily | BIGINT   | Number of unique active contract users on the given date.                                                                                                                        |
| total_active_user_count | BIGINT   | The cumulative number of unique contract users seen. Note that this number is not a simple running sum of `active_user_count_daily`, as one user can be active on multiple days. |

#### Response Example

<details><summary>Response</summary>
<div>

```Json
{
    "request_id": "d1b19b0f-ed01-4275-89a5-31d57f4e0ea8#56256",
    "code": 0,
    "message": "success.",
    "data": [
        {
            "stat_date": "2023-03-14T00:00:00Z",
            "active_user_count_daily": 210,
            "total_active_user_count": 210
        },
        {
            "stat_date": "2023-03-15T00:00:00Z",
            "active_user_count_daily": 4517,
            "total_active_user_count": 4665
        },
        {
            "stat_date": "2023-03-16T00:00:00Z",
            "active_user_count_daily": 1907,
            "total_active_user_count": 6434
        }
    ]
}
```
</div>
</details>
