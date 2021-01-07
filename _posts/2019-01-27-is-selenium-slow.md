---
layout: post
title:  "Is Selenium slow?"
description: "Why do you feel selenium is slow?"
author: philip
categories: [ Automation, Java ]
image: assets/images/2.jpg
tags: automation
---

Selenium is a browser automation tool and it is incredibly fast. But I have seen a lot of automation tests running terribly slow. It is ironic that all these slowness is being caused by incorrect attempt from automation engineers trying to tame the speed of Selenium. 

> ##### Selenium is not slow; but your application is 

Unless you tell Selenium to wait for an element, it won't and your automation test would fail with an exception. So how do you tell Selenium to wait?

#####  Thread Sleep - The ugly way

This is a static wait. You are stopping the execution thread for a particular amount of time. 
Lets say you put 5 seconds sleep time and suddenly your tests are passing. That particular element which always caused problem for you is no longer a worry. Your script waits for five seconds and Selenium identifies the element and your test is working fine. 

```java
    sleep(5);
    driver.findElement(By.id("username"));
```    

The disadvantage with this approach is that, the element may already have appeared in two seconds rather than the 5 seconds hard coded wait you supplied. In the worst case scenario, the element may take six or more seconds to appear in the page and your tests would fail. A mere two or three seconds we could have saved may not seem very much. But if you resort to thread sleep then it is almost certain that you would use it in many other places. All those lost seconds could accumulate to many minutes or even hours depending on the number of tests. 


#####  Try/Catch - The bad way

Though a bit unconventional, people use it anyways when they fail to find an element. It is often associated with a Thread Sleep in the catch block. 

```java
    try{
        driver.findElement(By.id("username"));
    } catch(Exception e) {
        sleep(3);
        driver.findElement(By.id("username"));
    }
```


##### Implicit or Explicit Waits - The best way

Both waits works on the same principle but with different implementations. It would  `wait until element is found` within a timeout period. 

Implicit wait is assigned to the driver and explicit wait is handled on the language bindings. 

`Warning:` Do not mix up implicit and explicit waits. It will really slow down your execution and result in unexpected timeouts. It is simple to understand why. The implicit wait is applied to the driver and explicit wait is controlled by your program. So when you have both of these waits present, they get mixed up while searching for an element. So just remember to use only one type of wait. 

Explicit waits give finer control over wait timeouts and expected conditions. You can increase the timeout for certain elements with explicit wait and wait for certain expected conditions to be met.






