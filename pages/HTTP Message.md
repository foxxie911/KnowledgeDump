- HTTP messages are the mechanism used to exchange data between a server and a client in the HTTP protocol.
- A HTTP is made up with 3 parts each ending with [[CRLF]] (`\r\n`)
	- Start Line
		- Has 3 parts
			- HTTP method
			- Request target
			- HTTP version

![Parts of HTTP Status Line](../assets/image_1736335992739_0.png)

	- Zero or more headers

![Parts of HTTP Header](../assets/image_1736336112425_0.png)
	- Body (Not available in GET requests)
- There are 2 types of HTTP Message
	1. Request Message
		- Sent by the clients
	2. Response Message
		- Sent by the server.
![Anatomy of HTTP Message](../assets/image_1736335156416_0.png)
-