# Topic 4.5: Exceptions

## Runtime Errors
* syntax errors vs. runtime errors
* **exceptions:** can be handled in some way; an abnormal or erroneous situation at runtime
* **error:** unrecoverable situations

## Throwing Exceptions
* exceptions can be thrown by the *runtime environment* or by the program
```java
public T pop() throws EmptyCollectionException
{
 if (isEmpty())
 throw new EmptyCollectionException(“Stack”);
 …
}
```

## Java Exceptions
* in java, an exception is an *object*
* there are exception classes
  * Exception > subclass: RuntimeException > subclass: NullPointerException
* examples: IllegalArgumentException, ArrayIndexOutOfBoundsException, IOException, NullPointerException
* can create our own exception object by ```extends Exception``` or one of its subclasses
```Java
public class EmptyCollectionException extends
 RuntimeException
{
/**
* Sets up this exception with an appropriate message.
* @param collection String representing name of collection
*/
 public EmptyCollectionException (String collection)
 {
 super (“The ” + collection + “ is empty.”);
 }
}
```

## Uncaught Exceptions
* if an exception is not handled, a standard error message is printed by Java runtime system and program is terminated

## Catching Exceptions
* to handle exception, a method, or runtime environemnet that detects error during execution ```throws``` an exception
* code that delas with exception is said to ```catch``` or ```handle``` it

### try-catch Statement
```Java
try
{ // try block: statements(s) that might cause an exception to
// be thrown
}
catch ( possible-exception-type e)
{ // catch clause: statements to handle the problem,
// referring to the exception object e
}
```
#### Try Block
* different ways:
  * put each line of code that might throw exception within its own try block and provide separate exception handlers
  * put all code in single try block and associate multiple handlers with it

#### Catch Block
* single catch block can handle more than one type of exception
* reduces code duplication and lessen overly broad exceptions
* just specify the types of exceptions the block can handle and separate each exception type with ```|```

#### How It Works
* when ```try-catch``` statement is executed, statements in ```try``` block are executed
* if *no exception* is thrown, processing continues after the try-catch statement
* if *exception* is thrown, control is immediately passed to the first ```catch``` clause whose specified exception corresponds to class of exception thrown
```Java
String filename = "/nosuchdir/myfilename";
try
{
  new File(filename).createNewFile();
 }
catch (IOException e)
{
  System.out.println("Unable to create" + filename + ":" + e.getMessage());
 }
// execution continues here
// output: Unable to create /nosuchdir/myfilename:The system cannot find the path specified
```

### Propagating the Exception
* the process if exception not caught and handled where occurs
* control is immediately returned to method that invoked the method that produced the exception
* if that method doesn't handle the exception (with try statement with catch clause)
* control returns to method that called it
* exception propagation continues until exception is caught and handled or until propagated out of main method, resulting in termination of program

### try-catch-finally
```
//general syntax
try { code }
catch(exception1) {statements}
catch(exception2) {statements}
catch(exception3|exception4){statements}
…
finally {statements}
```
#### Example
```java
private List<Integer> list;
private static final int SIZE = 10;
PrintWriter out = null;
try {
 System.out.println("Entered try statement");
 out = new PrintWriter(new FileWriter("OutFile.txt"));
 for (int i = 0; i < SIZE; i++)
 System.out.println("Value at: " + i + " = " + list.get(i));
}
catch(FileNotFoundException e) {
 System.err.println("FileNotFoundException: " +
 e.getMessage());
 // Ask for new filename
 throw new SampleException(e); }
catch(IOException e) {
 System.err.println("Caught IOException: " +
 e.getMessage());
}
finally {
 if (out != null) {
 System.out.println("Closing PrintWriter");
 out.close(); }
 else
 System.out.println("PrintWriter already closed");
}
```

#### Finally Block
* finally block executes when try block exits; executed even if unexpected exception occurs
* avoid having cleanup code accidentally bypassed by a return, continue or break
* good practice to put cleanup code in finally block even when no exceptions are anticipated
