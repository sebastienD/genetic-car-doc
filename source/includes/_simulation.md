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

Le body doit contenir un tableau d'objet comme le montre l'exemple ci-contre.

Ce endpoint permet de lancer l'évaluation d'une liste de véhicules.

La variable team est à remplacer par le nom de votre équipe.

<aside class="warning">
Le tableau ne doit pas contenir plus de 20 éléments.
</aside>

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "[\n    {\n      \"chassis\": {\n        \"vecteurs\": [\n          0.2421346,\n          0,\n          0.5412285,\n          0.46367344,\n          0,\n          0.40514365,\n          -0.7945067,\n          0.49603817,\n          -0.9156932,\n          0,\n          -1.0747113,\n          -0.8086521,\n          0,\n          -0.9599218,\n          1.0563881,\n          -0.81461006\n        ],\n        \"densite\": 251.71265\n      },\n      \"wheel1\": {\n        \"radius\": 0.35081068,\n        \"density\": 49.408844,\n        \"vertex\": 5\n      },\n      \"wheel2\": {\n        \"radius\": 0.4488887,\n        \"density\": 58.341553,\n        \"vertex\": 7\n      }\n    }\n]");
Request request = new Request.Builder()
  .url("http://genetic-car.herokuapp.com/simulation/evaluate/{team}")
  .post(body)
  .addHeader("content-type", "application/json")
  .addHeader("cache-control", "no-cache")
  .build();

Response response = client.newCall(request).execute();
```

```javascript
var data = JSON.stringify([
{
"chassis": {
    "vecteurs": [
    0.2421346,
    0,
    0.5412285,
    0.46367344,
    0,
    0.40514365,
    -0.7945067,
    0.49603817,
    -0.9156932,
    0,
    -1.0747113,
    -0.8086521,
    0,
    -0.9599218,
    1.0563881,
    -0.81461006
    ],
    "densite": 251.71265
},
"wheel1": {
    "radius": 0.35081068,
    "density": 49.408844,
    "vertex": 5
},
"wheel2": {
    "radius": 0.4488887,
    "density": 58.341553,
    "vertex": 7
}
}
]);

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
    if (this.readyState === 4) {
        console.log(this.responseText);
    }
});

xhr.open("POST", "http://genetic-car.herokuapp.com/simulation/evaluate/{team}");
xhr.setRequestHeader("content-type", "application/json");
xhr.setRequestHeader("cache-control", "no-cache");

xhr.send(data);
```

```go
package main

import (
    "fmt"
    "strings"
    "net/http"
    "io/ioutil"
)

func main() {

    url := "http://genetic-car.herokuapp.com/simulation/evaluate/{team}"

    payload := strings.NewReader("[\n    {\n      \"chassis\": {\n        \"vecteurs\": [\n          0.2421346,\n          0,\n          0.5412285,\n          0.46367344,\n          0,\n          0.40514365,\n          -0.7945067,\n          0.49603817,\n          -0.9156932,\n          0,\n          -1.0747113,\n          -0.8086521,\n          0,\n          -0.9599218,\n          1.0563881,\n          -0.81461006\n        ],\n        \"densite\": 251.71265\n      },\n      \"wheel1\": {\n        \"radius\": 0.35081068,\n        \"density\": 49.408844,\n        \"vertex\": 5\n      },\n      \"wheel2\": {\n        \"radius\": 0.4488887,\n        \"density\": 58.341553,\n        \"vertex\": 7\n      }\n    }\n]")

    req, _ := http.NewRequest("POST", url, payload)

    req.Header.Add("content-type", "application/json")
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

payload = "[\n    {\n      \"chassis\": {\n        \"vecteurs\": [\n          0.2421346,\n          0,\n          0.5412285,\n          0.46367344,\n          0,\n          0.40514365,\n          -0.7945067,\n          0.49603817,\n          -0.9156932,\n          0,\n          -1.0747113,\n          -0.8086521,\n          0,\n          -0.9599218,\n          1.0563881,\n          -0.81461006\n        ],\n        \"densite\": 251.71265\n      },\n      \"wheel1\": {\n        \"radius\": 0.35081068,\n        \"density\": 49.408844,\n        \"vertex\": 5\n      },\n      \"wheel2\": {\n        \"radius\": 0.4488887,\n        \"density\": 58.341553,\n        \"vertex\": 7\n      }\n    }\n]"

headers = {
    'content-type': "application/json",
    'cache-control': "no-cache"
}

conn.request("POST", "/simulation/evaluate/{team}", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

```csharp
var client = new RestClient("http://genetic-car.herokuapp.com/simulation/evaluate/{team}");
var request = new RestRequest(Method.POST);
request.AddHeader("cache-control", "no-cache");
request.AddHeader("content-type", "application/json");
request.AddParameter("application/json", "[\n    {\n      \"chassis\": {\n        \"vecteurs\": [\n          0.2421346,\n          0,\n          0.5412285,\n          0.46367344,\n          0,\n          0.40514365,\n          -0.7945067,\n          0.49603817,\n          -0.9156932,\n          0,\n          -1.0747113,\n          -0.8086521,\n          0,\n          -0.9599218,\n          1.0563881,\n          -0.81461006\n        ],\n        \"densite\": 251.71265\n      },\n      \"wheel1\": {\n        \"radius\": 0.35081068,\n        \"density\": 49.408844,\n        \"vertex\": 5\n      },\n      \"wheel2\": {\n        \"radius\": 0.4488887,\n        \"density\": 58.341553,\n        \"vertex\": 7\n      }\n    }\n]", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```ruby
require 'uri'
require 'net/http'

url = URI("http://genetic-car.herokuapp.com/simulation/evaluate/{team}")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Post.new(url)
request["content-type"] = 'application/json'
request["cache-control"] = 'no-cache'
request.body = "[\n    {\n      \"chassis\": {\n        \"vecteurs\": [\n          0.2421346,\n          0,\n          0.5412285,\n          0.46367344,\n          0,\n          0.40514365,\n          -0.7945067,\n          0.49603817,\n          -0.9156932,\n          0,\n          -1.0747113,\n          -0.8086521,\n          0,\n          -0.9599218,\n          1.0563881,\n          -0.81461006\n        ],\n        \"densite\": 251.71265\n      },\n      \"wheel1\": {\n        \"radius\": 0.35081068,\n        \"density\": 49.408844,\n        \"vertex\": 5\n      },\n      \"wheel2\": {\n        \"radius\": 0.4488887,\n        \"density\": 58.341553,\n        \"vertex\": 7\n      }\n    }\n]"

response = http.request(request)
puts response.read_body
```

<aside class="notice">
N'oubliez pas de remplacer <code>{team}</code> par le nom de votre équipe.
</aside>