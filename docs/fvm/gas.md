---
sidebar_position: 6
---

# Gas

Contracts provides daily information on gas usage across contracts on Filecoin Virtual Machine.

### Gas Usage

#### Description

The gas used to execute transactions on FEVM.

#### Request URL

```js
GET: /v2/fvm/gas_usage
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

url = "https://api.spacescope.io/v2/fvm/gas_usage?end_date=2023-03-16&start_date=2023-03-01"

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
  url := "https://api.spacescope.io/v2/fvm/gas_usage?end_date=2023-03-16&start_date=2023-03-01"
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
  'url': 'https://api.spacescope.io/v2/fvm/gas_usage?end_date=2023-03-16&start_date=2023-03-01',
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
curl --location --request GET 'https://api.spacescope.io/v2/fvm/gas_usage?end_date=2023-03-16&start_date=2023-03-01' \
--header 'authorization: Bearer <--Please replace your API key here-->'
```

</TabItem>
</Tabs>

</div>
</details>


#### Response Schema

| **Variable**   | **Type** | **Description**                                                                                      |
|----------------|----------|------------------------------------------------------------------------------------------------------|
| stat_date      | DATE     | Date, in YYYY-MM-DD.                                                                                 |
| gas_cost_daily | BIGINT   | Cost of gas used to execute transactions per day, denominated in FIL.                                |
| total_gas_cost | BIGINT   | Cumulative cost of gas used to execute transactions per day, denominated in FIL.                     |
| gas_used_daily | BIGINT   | Amount of gas used to execute transactions per day, denominated in billions of gas units.            |
| total_gas_used | BIGINT   | Cumulative amount of gas used to execute transactions per day, denominated in billions of gas units. |

#### Response Example

<details><summary>Response</summary>
<div>

```Json

{
    "request_id": "d1b19b0f-ed01-4275-89a5-31d57f4e0ea8#56257",
    "code": 0,
    "message": "success.",
    "data": [
        {
            "stat_date": "2023-03-14T00:00:00Z",
            "gas_cost_daily": 1588.76078162651,
            "total_gas_cost": 1588.76078162651,
            "gas_used_daily": 6256011058372,
            "total_gas_used": 6256011058372
        },
        {
            "stat_date": "2023-03-15T00:00:00Z",
            "gas_cost_daily": 18.1351667018025,
            "total_gas_cost": 1606.89594832831,
            "gas_used_daily": 10680453896311,
            "total_gas_used": 16936464954683
        },
        {
            "stat_date": "2023-03-16T00:00:00Z",
            "gas_cost_daily": 0,
            "total_gas_cost": 1606.89594832831,
            "gas_used_daily": 0,
            "total_gas_used": 16936464954683
        }
    ]
}
```
</div>
</details>
<hr />
