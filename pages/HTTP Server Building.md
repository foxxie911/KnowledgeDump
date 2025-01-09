- Here, Java is used to build the HTTP Server
- After creating and project and initializing git, Go to the `main.java` file.
- Bind a port to the server using `ServerSocket` package library of Java.
	- ```java
	  try {
	    ServerSocket serverSocket = new ServerSocket(4221);
	    // Since the tester restarts your program quite often, setting SO_REUSEADDR
	    // ensures that we don't run into 'Address already in use' errors
	    serverSocket.setReuseAddress(true);
	      
	    serverSocket.accept(); // Wait for connection from client.
	    System.out.println("accepted new connection");
	  } catch (IOException e) {
	    System.out.println("IOException: " + e.getMessage());
	  }
	  ```
	- Implement  [[HTTP Message]] management.
		- Server should be able to response to incoming requests from client and the response should vary from request to request.