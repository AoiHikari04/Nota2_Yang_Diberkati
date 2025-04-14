# DHCP

DORA
discover, offer, request, acknowledge

- first send discover to any server
- server reply with an offer
- request the actual IP 
- Server acknowledge the IP needed - if there is no more IP reply with DHCPNAK

in forms of UDP transport protocol

---
# DNS

- Map domain name to IP addresses
- Malicious DNS traffic can be detected through protocol analysis and the inspection of DNS

**DNS Lookup process**
- Check the local cache first
- if not found will query other higher level DNS servers (Recursive queries)
- If server need to find data at another zone, it will request of that data from an authoritative server for that zone (Zone transfer)
Step By Step:
1. user type any name into a browser
2. DNS query sent to dns server
3. DNS server match the name to its ip address
4. The DNS query response is sent back to client
5. DNS server matches the name with its IP address

- DNS uses UDP port 53
- DNS message format:
	- Question
	- Answer
	- Authority
	- Additional 

**DDNS**
- Dynamically link the IP address to name
- use if IP address changes based on DHCP server
- home server, home pc, devices that get the IP from dhcp server

---
# NAT





---
# File transfer and Sharing Services

**FTP and TFTP**
- FTP allows data transfer between client and server
- use to push and pull data from server
- Trivial FTP (TFTP) - simplified file transfer protocol using UDP port 69

**SMB**
- Server message block, sharing protocol that describe the structure of shared network
- client/server request-response protocol

---
# Email

**Email protocols** - this include :
- SMTP
- POP
- IMAP

**SMTP**
- sends and receive email
- client connect the SMTP process connects with a SMTP server at port 25
- Servers check the queue for messages and send any unsend message periodically

**POP3**
- retrieve mail from a mail server
- email are downloaded to client and removed from server
- TCP port 110

**IMAP**
- Another protocol that describe a method to retrieve email messages
- emails are downloaded but server keep the email until be manually deleted
- when user delete the messages, can sync and delete the message at the server

---
# HTTP

- When URL is typed into web browser, the browser will establishes the web services using HTTP protocol

**How web page is opened in browser:**
1. Browser interpret the three parts of URL
	- http ( the protocol )
	- www.youtube.com ( the server name )
	- index.html ( Specific filename )
2. Client initiates by sending a GET request to server asking for the filename
3. Server will response will the HTML code for the webpage
4. Browser decipher the HTML code and formats the page

**HTTP URL**
- can specify the port, query string, and fragment
- query strings are preceded by a " ? "
- fragments are preceded by a " # "

Example:
![[Pasted image 20250406234537.png]]

**HTTP Operation**
- Uses TCP port 80, flexible but not secure
- will use one of six methods
	- GET
	- POST
	- PUT
	- DELETE
	- OPTIONS
	- CONNECT

**HTTP Code status**
- numeric with first number indicating the type of message
- five status groups
	- **1xx** - informational
	- **2xx** - Success
	- **3xx** - Redirection
	- **4xx** - Client Error
	- **5xx** - Server Error

**HTTP/2**
- improve performance of HTTP by addressing the latency issues
- Few important features update
	- Multiplexing
	- Server PUSH
	- A binary protocol
	- Header compression

**HTTPS**
- Uses authentication and encryption to secure data as it travels between the client and the server
- Data stream are encrypted with Secure Socket Layer (SSL) or Transport Layer Security (TLS) before transported across network