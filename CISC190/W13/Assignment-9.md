# Below is my W13-16>1/2 assignment

## Task 1: Run Starter Code (5 Runs)

### Results

| Run | Output |
| :--- | :---: |
| **Run 1** | 2000 |
| **Run 2** | 2000 |
| **Run 3** | 2000 |
| **Run 4** | 2000 |
| **Run 5** | 2000 |

**Note:** Every run gave me 2000. I looked it up and learned that on my CPU, the code executes fast enough for t1 to finish before t2.

## Task 2: Fix using synchronized

```java
class Counter {
    int value = 0;

    synchronized void increment() {
        value++;
    }
}

public class Main {
    public static void main(String[] args) throws Exception {
        Counter counter = new Counter();

        Runnable task = () -> {
            for (int i = 0; i < 1000; i++) {
                counter.increment();
            }
        };

        Thread t1 = new Thread(task);
        Thread t2 = new Thread(task);

        t1.start();
        t2.start();

        t1.join();
        t2.join();

        System.out.println("Final Counter: " + counter.value);
    }
}
```
**Result:** Every output gave me 2000 consistently.

## Task 3: Increase Threads (5 Threads)

```java
class Counter {
    int value = 0;

    synchronized void increment() {
        value++;
    }
}

public class Main {
    public static void main(String[] args) throws Exception {
        Counter counter = new Counter();

        Runnable task = () -> {
            for (int i = 0; i < 1000; i++) {
                counter.increment();
            }
        };

        Thread[] threads = new Thread[5];

        for (int i = 0; i < threads.length; i++) {
            threads[i] = new Thread(task);
            threads[i].start();
        }

        for (int i = 0; i < threads.length; i++) {
            threads[i].join();
        }

        System.out.println("Final Counter: " + counter.value);
    }
}
```
**Result:** Every output gave me 5000 consistently.

## Task 4: Add Sleep (Visualizing Parallelism)
```java
public class Main {
    public static void main(String[] args) throws Exception {
        Runnable task = () -> {
            for (int i = 1; i <= 5; i++) {
                System.out.println(Thread.currentThread().getName() + " : " + i);
                try {
                    Thread.sleep(500);
                } catch (InterruptedException e) {}
            }
        };

        Thread[] threads = new Thread[5];

        for (int i = 0; i < threads.length; i++) {
            threads[i] = new Thread(task);
            threads[i].start();
        }

        for (int i = 0; i < threads.length; i++) {
            threads[i].join();
        }
    }
}
```
**Result:** I got 5 threads displayed at random in my console.

## Reflection Questions:
### 1. Two threads are looking at a number at the same time; therefore, both threads will save the number, and because of that, one count is lost.
### 2. A race condition is when multiple threads race to change the same variable at the same time, resulting in a messed-up count.
### 3. Synchronized allows only one thread to update the counter at a time, while the other threads are in a queue.
### 4. No, more threads do not mean faster execution. It's like too many cooks in the kitchen.
#
#
#
#
#
# Below is my W13-16>2/2 assignment
```java
import java.util.concurrent.*;
import java.util.*;

public class Main {
    public static void main(String[] args) throws Exception {

        ExecutorService executor = Executors.newFixedThreadPool(3);

        List<Callable<Integer>> tasks = List.of(
                () -> { Thread.sleep(3000); return 10; },
                () -> { Thread.sleep(1000); return 20; },
                () -> { Thread.sleep(2000); return 30; }
        );

        int fastestResult = executor.invokeAny(tasks);
        System.out.println("Fastest Result: " + fastestResult);

        List<Future<Integer>> results = executor.invokeAll(tasks);

        int sum = 0;
        for (Future<Integer> f : results) {
            sum += f.get();
        }

        System.out.println("Sum of all results: " + sum);

        CompletionService<Integer> service =
                new ExecutorCompletionService<>(executor);

        for (Callable<Integer> task : tasks) {
            service.submit(task);
        }

        System.out.println("Results in completion order:");
        for (int i = 0; i < tasks.size(); i++) {
            Future<Integer> result = service.take();
            System.out.println(result.get());
        }

        long start = System.currentTimeMillis();

        List<Future<Integer>> experimentResults = executor.invokeAll(tasks);
        int total = 0;
        for (Future<Integer> f : experimentResults) {
            total += f.get();
        }

        long end = System.currentTimeMillis();
        System.out.println("Time: " + (end - start));

        List<Callable<String>> tasksF = List.of(
                () -> { Thread.sleep(3000); return "Database query (3s)"; },
                () -> { Thread.sleep(1000); return "Cache lookup (1s)"; },
                () -> { Thread.sleep(2000); return "API call (2s)"; }
        );

        long startFast = System.currentTimeMillis();
        String fastestTask = executor.invokeAny(tasksF);
        long endFast = System.currentTimeMillis();
        System.out.println("Fastest task: " + fastestTask);
        System.out.println("Time: " + (endFast - startFast));

        long startAll = System.currentTimeMillis();
        CompletionService<String> serviceF =
                new ExecutorCompletionService<>(executor);

        for (Callable<String> task : tasksF) {
            serviceF.submit(task);
        }

        System.out.println("Tasks in completion order:");
        for (int i = 0; i < tasksF.size(); i++) {
            Future<String> result = serviceF.take();
            System.out.println(result.get());
        }
        long endAll = System.currentTimeMillis();
        System.out.println("Time: " + (endAll - startAll));

        executor.shutdown();
    }
}
```

## Reflection Questions:
### 1. `invokeAny` only cares about the first task that finishes. Once a task finishes, it'll just grab that one answer and cancel the rest of them.
### 2. You use `invokeAll` when you need every task to finish before moving on to the rest of the code.
### 3. `CompletionService` puts all the results from the tasks in a queue. Once the fastest task finishes, the program has access to that information while the slower tasks that take more time to complete in the background and will be available once finished.
### 4. No. You just end up creating more tasks for the program, and essentially slow it down since the program has to bounce between a higher number of tasks that need to be completed.
