# HTTP Request Relay Server
Make a HTTP request via a relay server.

This is useful for situations where you need control over the outbound IP address or in cases where the requests can't be made from a browser.

Use cases
- Cloudflare worker / pages function
- API server that only accepts certain whitelisted IP addresses

## Development
```
go run main.go
```


## Example Usage
```js
const url = 'http://localhost:8080/relay'; // URL of your Go relay server

// Data to be relayed
const relayData = {
    url: 'https://api.example.com/posts', // Target API URL
    method: 'POST',
    headers: {
        'Content-Type': 'application/json'
    },
    body: JSON.stringify({
        title: 'foo',
        body: 'bar',
        userId: 1
    })
};

fetch(url, {
    method: 'POST',
    headers: {
        'Content-Type': 'application/json'
    },
    body: JSON.stringify(relayData)
})
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.error('Error:', error));
```