---
title: "Volatile Keyord"
date: 2020-04-20T10:37:36-04:00
---
The *volatile* keyword in java verifies that the variable with that keyword will not be cached by a thread locally, but will be directly read from the main-memory. 
This means, it is a synchronized variable and at any given point of time ALL threads will see the same copy of it. 

```java
public class VolatileTest {
    volatile static int counter = 0;
    public static void main(String[] args) {
        Thread t1 = new Thread(() -> counter++);
        Thread t2 = new Thread(() -> System.out.println(counter));
        t1.start();
        t2.start();
    }
}
```
```text
output is 1 ( not necessarily but considering t1 modifies counter first )
```