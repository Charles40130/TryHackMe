

---
HTTP Request
- Composed of an header and a body


|   |   |   |
|---|---|---|
|**Request Header**|**Example**|**Description**|
|Host|`Host: tryhackme.com`|Specifies the name of the web server the request is for.|
|User-Agent|`User-Agent: Mozilla/5.0`|Shares information about the web browser the request is coming from.|
|Referer|`Referer: https://www.google.com/`|Indicates the URL from which the request came from.|
|Cookie|`Cookie: user_type=student; room=introtowebapplication; room_status=in_progress`|Information the web server previously asked the web browser to store is held in cookies.|
|Content-Type|`Content-Type: application/json`|Describes what type or format of data is in the request.|-


- Request body :
	- data

Many format of the data:
- URL encoded(application/x-www-form-urlencoded)
	- data structured in pairs of key and value ( key = value) and separated by `&` symbol. (key1=value1&key2=value2)
- Form Data (multipart/form-data)
	- multiple data blocks , each block is separated by a boundary string
- JSON (application/json)
	- data formatted in pairs of name : value 
- XML (application/xml)
	- data structured inside labels called tags which have an opening and closing


---
## HTTP Response
- first line = Status line , give :
	- HTTP Version : version of http used
	- Status code : three digit number showing the outcome of your request
	- Reason phrase : short message explaning the status code

**Status codes and reason phrases

**Informational Responses (100-199)**  
These codes mean the server has received part of the request and is waiting for the rest. It’s a "keep going" signal.

**Successful Responses (200-299)**  
These codes mean everything worked as expected. The server processed the request and sent back the requested data.

**Redirection Messages (300-399)**  
These codes tell you that the resource you requested has moved to a different location, usually providing the new URL.

**Client Error Responses (400-499)**  
These codes indicate a problem with the request. Maybe the URL is wrong, or you’re missing some required info, like authentication.

**Server Error Responses (500-599)**  
These codes mean the server encountered an error while trying to fulfil the request. These are usually server-side issues and not the client’s fault.

**100 (Continue)**  
The server got the first part of the request and is ready for the rest.

**200 (OK)**  
The request was successful, and the server is sending back the requested resource.

**301 (Moved Permanently)**  
The resource you’re requesting has been permanently moved to a new URL. Use the new URL from now on.

**404 (Not Found)**  
The server couldn’t find the resource at the given URL. Double-check that you’ve got the right address.

**500 (Internal Server Error)**  
Something went wrong on the server’s end, and it couldn’t process your request.

---
## HTTP Response header

It is composed of:
- Date 
	- Example: `Date: Fri, 23 Aug 2024 10:43:21 GMT`
- Content-Type
	- Example: `Content-Type: text/html; charset=utf-8`
 - Server
	 - Example: `Server: nginx`

Other common response headers
- Set-Cookie ( keep information between the server and the browser)
	- Example: `Set-Cookie: sessionId=38af1337es7a8`
	- used for sessions ( authentification) , save préférences of a web site, save a basket
	- Cookie can be stolen, we need to had "flags"
		- `HttpOnly` (protect against steal via **XSS**) => prevent javascript access to the cookie
		 `Set-Cookie: sessionId=38af1337es7a8; Secure` 
		- `Secure` (protect against interception )
			=> cookie only send via HTTPS
			`Set-Cookie: sessionId=38af1337es7a8; Secure`
		- `SameSite` (protect against attacs CSRF)

- Cache-Control
	- Example: `Cache-Control: max-age=600`
	- defined how long the browser can be cache a resource before reasking it
- Location
	- Example: `Location: /index.html`


---
## Security Headers
- https://securityheaders.com/ : website to check security headers of a website
- Content-Security-Policy (CSP header)
	- controls what resources the browser is allowed to load
		- scripts
		- styles
		- images
		- frames
		- fonts
		- APIs
		- etc...
- Strict-Transport-Security (HSTS)
	- forces browsers to use HTTPS only for your site

- X-Content-Type-Options
	-  prevents MIME type sniffing by browsers
- Referrer-Policy
	- controls what information is sent in the `Referer` header when navigating to another site