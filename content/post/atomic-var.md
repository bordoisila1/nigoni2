---
title: "Atomic Variables in Java"
date: 2020-04-20T13:15:57-04:00
---
Atomic variables are variables that act just the way any volatile variable would work. 
This means, every subsequent get after a set will have the same value for all threads. 
```java
import java.util.concurrent.atomic.AtomicInteger;

public class AtomicVarTest {
    private static AtomicInteger atomicInt = new AtomicInteger(0);
    public static void increment() {
        atomicInt.incrementAndGet();
    }
    public static void decrement() {
        atomicInt.decrementAndGet();
    }
    public static int get() {
        return atomicInt.get();
    }
    public static void main(String[] args) {
        Thread t1 = new Thread(() -> {
            increment();
            System.out.println("Value from t1 " + get());
        });

        Thread t2 = new Thread(() -> {
            increment();
            System.out.println("Value from t2 " + get());
        });

        t1.start();
        t2.start();
    }
}
```

