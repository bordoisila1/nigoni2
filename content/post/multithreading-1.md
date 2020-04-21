---
title: "Multithreading in Java Series - 1"
date: 2020-04-20T18:28:16-04:00
---
Hey everyone, this is the first of the many articles that I am about to write regarding Multithreading in Java. 
# What is Multithreading ? 
A way to have multiple threads work in your application to have maximum CPU utilization with minimum interference.
Did I say that you don't always have to make your users wait for that loooong... network call ?
 
# Why do we need Multithreading ?
1. Better CPU utilization
2. Better responsiveness of the application

# Types of Concurrency Models 
1. **Shared State** - Well, share, share and, share. Just make sure it's not a nightmare !
2. **Shared nothing** - Perhaps you can exchange those immutable objects that you created but didn't know where to use ?
3. **Parallel workers** - Oh wait, you have those subordinates that you can delegate the work to ? Go ahead. But make sure they don't fight over that single file in your cabinet !

### Checkout this Race Condition simulation
Threads are in a race of getting their chance at executing the critical section of code, and the order in which threads access this critical section determines the output of the program.
```java
public class RaceConditionThread {
    static int x = 0;

    public static void main(String[] args) {
        for(int i = 0; i < 20; i++) {
            new Thread("" + i){
                public void run() {
                    System.out.println("Thread " + getName() + " is accessing x");
                    x++;
                    System.out.println("x in Thread " + getName() + " is " + x);
                }
            }.start();
        }
    }
}
```