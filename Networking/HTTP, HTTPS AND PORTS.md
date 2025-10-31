# HTTP/HTTPS Red Teaming Master Guide

## HTTP (HyperText Transfer Protocol)
**The Foundation of Web Communication**

### Key Characteristics:
- **Stateless Protocol**: Each request is independent (no memory between requests)
- **Client-Server Model**: Browser (client) requests, Web Server responds
- **Text-Based**: Human-readable format (unlike binary protocols)
- **Port 80**: Default HTTP port

## HTTP Request Methods (Verbs)
**What the Client Wants to Do:**

| Method | Description | Red Team Use |
|--------|-------------|--------------|
| **GET** | Retrieve data from server | Enumeration, reconnaissance |
| **POST** | Submit data to server | Data injection, authentication attacks |
| **PUT** | Update existing resource | File upload, overwrite files |
| **DELETE** | Remove resource | Data destruction, testing permissions |
| **HEAD** | Get headers only | Stealthy reconnaissance |
| **OPTIONS** | Discover supported methods | Service enumeration |
| **TRACE** | Echo back received request | Debugging, XST attacks |
| **PATCH** | Partial resource update | Data modification |

## HTTP Status Codes
**The Server's Response Language:**

### 1xx (Informational)
- Request received, continuing process

### 2xx (Success)
- **200 OK**: Standard success response
- **201 Created**: Resource created successfully
- **204 No Content**: Success but no content to return

### 3xx (Redirection)
- **301 Moved Permanently**: URL permanently changed
- **302 Found**: Temporary redirection
- **304 Not Modified**: Use cached version

### 4xx (Client Error)
- **400 Bad Request**: Malformed request syntax
- **401 Unauthorized**: Authentication required
- **403 Forbidden**: Authenticated but not authorized
- **404 Not Found**: Resource doesn't exist
- **418 I'm a teapot**: Easter egg (RFC 2324)

### 5xx (Server Error)
- **500 Internal Server Error**: Generic server error
- **502 Bad Gateway**: Upstream server issues
- **503 Service Unavailable**: Server overloaded or down

## HTTP Headers
**The Metadata of Web Requests:**

### Common Request Headers:
- **User-Agent**: Identifies the client software
- **Host**: Specifies the domain being requested
- **Cookie**: Sends stored session data to server
- **Authorization**: Credentials for authenticated requests
- **Content-Type**: Format of the request body

### Common Response Headers:
- **Set-Cookie**: Server instructs client to store session data
- **Content-Type**: Format of the response body
- **Server**: Information about the server software
- **Location**: URL for redirection responses

### Security Headers (Defensive):
- **Strict-Transport-Security**: Enforces HTTPS
- **Content-Security-Policy**: Prevents XSS
- **X-Frame-Options**: Prevents clickjacking
- **X-Content-Type-Options**: Prevents MIME sniffing

## HTTPS (HTTP Secure)
**Encrypted Web Communication:**

- **Port 443**: Default HTTPS port
- **TLS/SSL Encryption**: All data encrypted in transit
- **Certificate Validation**: Ensures you're talking to the real server
- **Same HTTP semantics**: Just wrapped in encryption

## Common Ports & Services
**Essential Port Reference:**

| Port | Service | Purpose |
|------|---------|---------|
| **20/21** | FTP | File Transfer Protocol |
| **22** | SSH | Secure Shell - Remote administration |
| **23** | Telnet | Unencrypted remote login |
| **25** | SMTP | Email sending |
| **53** | DNS | Domain Name System |
| **80** | HTTP | Web traffic |
| **110** | POP3 | Email retrieval |
| **123** | NTP | Network Time Protocol |
| **135** | RPC | Remote Procedure Call |
| **139/445** | SMB | Windows file sharing |
| **143** | IMAP | Email management |
| **443** | HTTPS | Secure web traffic |
| **993** | IMAPS | Secure IMAP |
| **995** | POP3S | Secure POP3 |
| **1433** | MSSQL | Microsoft SQL Server |
| **3306** | MySQL | MySQL Database |
| **3389** | RDP | Remote Desktop Protocol |
| **5432** | PostgreSQL | PostgreSQL Database |
| **5900** | VNC | Virtual Network Computing |

## Hands-On Labs

### Exercise 1: Browser Developer Tools Analysis

1. Open Chrome/Firefox and press F12 to open Developer Tools
2. Go to Network tab and ensure recording is enabled (red circle)
3. Visit http://httpbin.org/get
4. Analyze the request/response in Headers tab:
   - Request Headers: User-Agent, Accept, Host
   - Response Headers: Content-Type, Server, Date
   - Status Code: 200 OK 



## Exercise 2: curl - The Red Teamer's Web Browser


#### Basic GET request with verbose output
```curl -v http://httpbin.org/get```

#### Custom headers for evasion
```curl -H "User-Agent: RedTeamBot" -H "X-Custom-Header: test" http://httpbin.org/headers```

#### POST request with data
```curl -X POST -d "username=admin&password=test" http://httpbin.org/post```

#### Follow redirects automatically
```curl -L http://httpbin.org/redirect/2```

#### Save and use cookies
```curl -c cookies.txt http://httpbin.org/cookies/set/session/abc123```
```curl -b cookies.txt http://httpbin.org/cookies```



## Exercise 3: Wireshark HTTP Analysis


1. Start Wireshark with filter: `http && host httpbin.org`
2. Make requests using curl or browser
3. Analyze unencrypted HTTP traffic:
   - Find the GET request
   - Locate the 200 OK response
   - Examine headers in plain text



## Exercise 4: HTTPS Analysis

1. Wireshark filter: `tls && host httpbin.org`
2. Visit https://httpbin.org/get
3. Observe encrypted traffic - you can't read the content!
4. Notice the TLS handshake before HTTP communication

## RED TEAMER PERSPECTIVE
### Why HTTP/HTTPS Knowledge is Critical:

#### Reconnaissance:

* Server Fingerprinting: Identify web server software via headers

* Application Mapping: Discover endpoints and functionality

* Technology Detection: Identify frameworks via headers and cookies

#### Attack Vectors:

* Header Manipulation: Modify User-Agent, Cookies, Referer

* HTTP Method Abuse: PUT/DELETE for file upload/deletion

* Parameter Tampering: Modify GET/POST parameters

* Session Hijacking: Steal and reuse cookies

#### Web Service Assessment:

* Port 80/443: Always the first ports to check

* API Endpoints: Modern apps use HTTP APIs extensively

* Authentication Bypass: Manipulate auth headers and cookies

## ESSENTIAL CURL FLAGS FOR RED TEAMING
### Stealth and evasion
```
curl -A "Mozilla/5.0"          # Spoof User-Agent
curl --referer "https://google.com"  # Fake referer
```
### Authentication testing
```
curl -u admin:password         # Basic auth
curl -H "Authorization: Bearer token"  # Bearer token
```
### Proxy support
```
curl -x http://proxy:8080      # Use proxy
```
### Timing and performance
```
curl -w "@curl-format.txt"     # Custom output format
```

## Status Code Quick Reference:
* 200: Success

* 301/302: Redirect

* 401: Authentication required

* 403: Forbidden

* 404: Not found

* 500: Server error

### Critical Ports:
* 80: HTTP

* 443: HTTPS

* 8080: HTTP Alternate

* 8443: HTTPS Alternate

*Remember:* Always use these techniques only on systems you own or have explicit permission to test. Unauthorized testing is illegal.
