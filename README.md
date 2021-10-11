# Host Header Injection

Purpose of host header injection is to identify which back-end component client want to communicate.

It is mandatory request header as of HTTP/1.1

Http host header exploite vulnerable website that handle the value of host header in an unsafe way.

## [How to Test Host Header attack](https://portswigger.net/web-security/host-header/exploiting)

1. Supply arbitary Host Header: `Host: Bing.com`

2. Inject duplicate Host Header: 
```
Host: example.com
Host: Bing.com
````

3. Supply absolute URL: 
```
GET http://example.com/index /Http1.1
Host: Bing.com 
```

4. Add line wrapping
```
GET /example HTTP/1.1
 Host: Bing.com
Host: example.com
```
5. Inject Host override header: 

```
GET example.com/index /Http1.1
Host: example.com
X-Forwarded-Host: Bing.com
```

## ⛑️ How to prevent

- Protect absolute URLs
- Validate the Host header
- Don't support Host override headers
- Whitelist permitted domains


## Refrence

- https://portswigger.net/web-security/host-header
