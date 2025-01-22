### Error hierarchy of Java
collapsed:: true
	- All the errors that java catches are descendants of Throwable class.
	- Throwable is divided into two sections
		- **Error**
			- Describes internal errors of Java Runtime system.
			- There is nothing to do about it rather than letting the user know that something wrong has happened and close the program.
		- **Exception**
			- It further divided into two parts
				- **Runtime Exception**
					- Exceptions such a bad cast, null pointer array, index out of bounds are runtime exception
					- These exceptions occurs because of bad code.
					- Fixing code rather than handling these exception is the best thing to do while encounter one such exception.
					- "If it is a RuntimeException, it is your fault works very well
				- **I/O Exception**
					- These are the exception such as trying to read past the end of a file, trying to open a file that doesn't exist, trying to find a class object for a string that does not denote an existing class etc.
					- This are the exception that should be handled by the developer.
		- **Error** and **Runtime exception** are called **unchecked exception**.
		- The **I/O Exception** are called **checked exception** as the compiler checks if developer has added an exception handler for that.
- ### Throwing exceptions
  collapsed:: true
	- A method can throw a particular exception is notified to the compiler by `throws` specifier.
	  ```java
	  public Image loadImage(String s) throws FileNotFoundException{...}
	  ```
	- Multiple exception can be thrown using comma.
	  ```java
	  public Image loadImage(String s) throws FileNotFoundException, EOFException{...}
	  ```
	- While overriding a method from superclass, it is not possible to declare more general exception than the superclass method have declared but declaring more specific method is completely fine.
	- If there is a predefined exception class for the expected exception then the steps of throwing are easy.
		- Find an appropriate exception class.
		- Make an object of that class.
		- Throw the exception with `throw` specifier.
		- After following the steps the code should look like
		  
		  ```java
		  String readData(Scanner in) throws EOFException{
		  	...
		      while(...){
		      	if(!in.hasNext()){
		          	if(n < len) throw new EOFException();
		          }
		      }
		  }
		  ```
	- If there is no existing exception that clearly describes the problem, it is necessary to create a new exception that does that.
		- Create the new exception extending the exception, throwable or any other exception class (the more specific , the better)
		- It is a custom to add two constructors, a default constructor and another constructor that contains  a message. (The `toString()` method of the Throwable superclass returns a detailed message)
		  
		  ```java
		  class FileFormatException extends IOException{
		    public FileFormatException(){}
		    public FileFormatException(String gripe){
		      super(gripe);
		    }
		  }
		  ```
-