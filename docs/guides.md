---
sidebar_position: 2
---

# Guides

## Authentication

All HTTP requests made against the Spacescope API must be validated with an API key.

Please [sign in](https://spacescope.io/sign/in) to view your API key. Don't have an account? [Register](https://spacescope.io/sign/up/email) now to activate your API key for free! 


## Quick Start

#### Quick Start Code Example


<details open><summary>Code</summary>
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

#### Return Data Example

All endpoints return data in JSON format with the results of your query under `data` if the call is successful.

<details open><summary>Response</summary>
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

## Errors

#### HTTP Status Codes

The API uses standard HTTP status codes to indicate the success or failure of an API call.
- `200 (OK)`: Standard response for successful HTTP requests. The actual response will depend on the request method used.
- `400 (Bad Request)`: The server cannot or will not process the request due to an apparent client error.
- `401 (Unauthorized)`: The user does not have valid authentication credentials for the target resource.
- `500 (Internal Server Error)`: A generic error message is given when an unexpected condition is encountered, and no other error message is suitable.
- `502 (Bad Gateway)`:  The server was acting as a gateway or proxy and received an invalid response from the upstream server.


#### Error Response Codes

In the event that an error occurs, you may reference the `code` and `message` properties. One of the API error codes below will be returned if applicable.


| **HTTP Status** | **Code** | **Message**                                                  |
| :-------------- | :------- | :----------------------------------------------------------- |
| 401             | 10011    | The token format error. It should have 'Bearer $token' set in the 'authorization' header. |
| 401             | 10012    | The token has expired.                                       |
| 200             | 30001    | Spacescope API forbidden: quota limited / historical limited / API limited.                                   |
| 200             | 30002    | Spacescope API parameters error.                             |
| 200             | 30003    | Spacescope API internal server error.                        |
| 200             | 30004    | Spacescope API data are not ready yet.                       |


## Daily Update Time
If unspecified, the daily updates (for T-1 data) will normally be available at `09:00 PM UTC` every day. 

For example, the data for `July 1, 2022 UTC` should be ready at `09:00 PM, July 2, 2022 UTC`.
