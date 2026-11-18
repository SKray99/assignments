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
