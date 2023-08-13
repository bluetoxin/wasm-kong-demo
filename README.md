# Docker WASM Kong Template (GO)
Docker template for "https://github.com/Kong/proxy-wasm-go-filter-template"

# Synopsis  
Clone this repository:  
```
git clone --recursive git@github.com:bluetoxin/wasm-kong-demo.git
cd wasm-kong-demo
```
Once you're in the cloned directory, initiate the Docker containers' creation using the following command:
```
docker-compose up -d --build
```
Send a test request to the proxy port through cURL:
```
curl 127.0.0.1 -I
```
Your response will resemble the example below:

```
HTTP/1.1 200 OK
Content-Type: text/html; charset=UTF-8
Content-Length: 756
Connection: keep-alive
Date: Sun, 13 Aug 2023 00:33:29 GMT
Server: Apache/2.2.22 (Debian)
Last-Modified: Thu, 29 Jun 2017 13:36:05 GMT
ETag: "300e24-2f4-5531961e15b40"
Accept-Ranges: bytes
Vary: Accept-Encoding
X-Kong-Upstream-Latency: 2
X-Kong-Proxy-Latency: 53
Via: kong/3.4.0
X-Greeting: Hello from Kong using WebAssembly!
```
The last header, X-Greeting, is appended by the WebAssembly module:
```
X-Greeting: Hello from Kong using WebAssembly!
```
