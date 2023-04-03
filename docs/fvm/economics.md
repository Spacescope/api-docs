---
sidebar_position: 6
---

# Economics

Economics provides daily information about the economic value of contracts on the Filecoin Virtual Machine.


### Total Value Locked

#### Description

The total value locked of all FEVM contracts, denominated in FIL.

#### Request URL

```js
GET: /v2/fvm/total_value_locked
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

url = "https://api.spacescope.io/v2/fvm/total_value_locked?end_date=2023-03-16&start_date=2023-03-01"

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
  url := "https://api.spacescope.io/v2/fvm/total_value_locked?end_date=2023-03-16&start_date=2023-03-01"
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
  'url': 'https://api.spacescope.io/v2/fvm/total_value_locked?end_date=2023-03-16&start_date=2023-03-01',
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
curl --location --request GET 'https://api.spacescope.io/v2/fvm/total_value_locked?end_date=2023-03-16&start_date=2023-03-01' \
--header 'authorization: Bearer <--Please replace your API key here-->'
```

</TabItem>
</Tabs>

</div>
</details>


#### Response Schema

| **Variable**         | **Type** | **Description**                                                              |
|----------------------|----------|------------------------------------------------------------------------------|
| stat_date            | DATE     | Date, in YYYY-MM-DD.                                                         |
| total_value_locked   | BIGINT   | The total value locked by all FEVM contracts per day, denominated in FIL. In this context, total value locked refers to the sum of the balances of all contracts.   |
<!-- | total_value_received | BIGINT   | The total value received across FEVM contracts each day, denominated in FIL. |
| total_value_sent     | BIGINT   | The total value sent across all FEVM contracts each day, denominated in FIL. | -->

#### Response Example

<details><summary>Response</summary>
<div>

```Json
{
    "request_id": "d1b19b0f-ed01-4275-89a5-31d57f4e0ea8#56254",
    "code": 0,
    "message": "success.",
    "data": [
        {
            "stat_date": "2023-03-14T00:00:00Z",
            "total_value_locked": 273.002,
            "total_value_received": 274.182,
            "total_value_sent": -1.18
        },
        {
            "stat_date": "2023-03-15T00:00:00Z",
            "total_value_locked": 1744.42538415519,
            "total_value_received": 4082.02131849924,
            "total_value_sent": -2337.59593434405
        },
        {
            "stat_date": "2023-03-16T00:00:00Z",
            "total_value_locked": 1615.37416151069,
            "total_value_received": 4203.55695706547,
            "total_value_sent": -2588.18279555478
        }
    ]
}
```
</div>
</details>