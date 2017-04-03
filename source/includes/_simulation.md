# Simulation

## Champions

<coderest>
  <span class="verb">GET</span>
  <span class="uri">/simulation/champions/{team}</span>
</coderest>

Ce endpoint permet de retourner les champions de toutes les équipes.

La variable team est à remplacer par le nom de votre équipe.

```java
OkHttpClient client = new OkHttpClient();

Request request = new Request.Builder()
  .url("http://genetic-car.herokuapp.com/simulation/champions/{team}")
  .get()
  .addHeader("cache-control", "no-cache")
  .build();

Response response = client.newCall(request).execute();
```

```javascript
var data = null;

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("GET", "http://genetic-car.herokuapp.com/simulation/champions/{team}");
xhr.setRequestHeader("cache-control", "no-cache");
xhr.setRequestHeader("postman-token", "c4171148-1510-64ca-4b90-23ba1583efd6");

xhr.send(data);
```

```go
package main

import (
	"fmt"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "http://genetic-car.herokuapp.com/simulation/champions/{team}"

	req, _ := http.NewRequest("GET", url, nil)

	req.Header.Add("cache-control", "no-cache")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```python
import http.client

conn = http.client.HTTPConnection("genetic-car.herokuapp.com")

headers = {
    'cache-control': "no-cache"
    }

conn.request("GET", "/simulation/champions/{team}", headers=headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```csharp
var client = new RestClient("http://genetic-car.herokuapp.com/simulation/champions/{team}");
var request = new RestRequest(Method.GET);
request.AddHeader("cache-control", "no-cache");
IRestResponse response = client.Execute(request);
```

```ruby
require 'uri'
require 'net/http'

url = URI("http://genetic-car.herokuapp.com/simulation/champions/{team}")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)
request["cache-control"] = 'no-cache'

response = http.request(request)
puts response.read_body
```

<aside class="notice">
N'oubliez pas de remplacer <code>{team}</code> par le nom de votre équipe.
</aside>

## Evaluation

<coderest>
  <span class="verb">POST</span>
  <span class="uri">/simulation/evaluate/{team}</span>
</coderest>

Ce endpoint permet de lancer l'évaluation d'une liste de véhicules.

La variable team est à remplacer par le nom de votre équipe.

  ```java
  ```
  ```javascript
  ```
  ```go
  ```
  ```python
  ```
  ```csharp
  ```ruby
  
<aside class="notice">
N'oubliez pas de remplacer <code>{team}</code> par le nom de votre équipe.
</aside>