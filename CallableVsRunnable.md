# Runnable vs Callable

|                    | Runnable                                      | Callable                                       |
|--------------------|-----------------------------------------------|------------------------------------------------|
| Introduced In      | Java 1.0                                      | Java 1.5                                       |
| Package            | java.lang                                     | java.util.concurrent                           |
| Method             | run()                                         | call()                                         |
| Return Value       | Cannot return a result                        | Returns a result of type V                     |
| Exception Handling | Cannot throw checked exceptions               | Can throw checked exceptions                   |
| Execution          | Can be executed by Thread or Executor Service | Must be executed by Executor service           |
| Use Case           | Fire and forgot tasks                         | Tasks requiring a result or execution handling |

# Sample code

## Using Runnable with Thread

````java
Runnable task = () -> System.out.println("Executing Runnable task");
Thread thread = new Thread(task);
thread.start();
````

## Using Callable with ExecutorService

```java
Callable<String> task = () -> {
    // Simulate some computation
    Thread.sleep(1000);
    return "Result from Callable";
};

ExecutorService executor = Executors.newSingleThreadExecutor();
Future<String> future = executor.submit(task);

// Retrieve the result
try {
    String result = future.get();
    System.out.println(result);
} catch (InterruptedException | ExecutionException e) {
    e.printStackTrace();
} finally {
    executor.shutdown();
}
```

# References
- [Difference Between Callable and Runnable in Java](https://www.geeksforgeeks.org/difference-between-callable-and-runnable-in-java/)

