---
layout: post
title:  "Should you use a static WebDriver?"
description: "An article about using static WebDriver with Selenium"
author: philip
categories: [ Selenium, WebDriver]
image: assets/images/staticvsinstant.jpeg
tags: [automation]
---

During the initial stages of my automation learning, one of the first mistakes I did was using a static WebDriver. It seemed to be easy to go with static drivers as I didn't have to bother with class extension or dependency injections. I knew static was bad, but then thought, I will deal with it later.

Later, when I came to implement parallel runs, it started getting complicated, I got a lot of WebDriver related errors because the same instance of driver was shared across different parallel threads. I had to undergo a painful process of unpicking each of those errors and make corrections. Wish I had been wiser!

##### A static Implementation

```java:
private static WebDriver driver;

public static WebDriver getDriver(){
    return driver;
}
```

I have omitted the detailed implementation here for brevity but you get the idea how it can be used. 
If static WebDriver is bad, what are the other options? Let's explore a few. 


##### Option one: Dependency Injection

Scary it may sound, but dependency injection is quite simple in concept. A dependeny injection framework will initiate an instance of a class and supply the same instance to all the classes where it is called. This would eliminate the tight coupling between classes and the whole relations with classes become quite simple to maintain. 

##### Option two: Class extension

With this option, you just extend a class containing the WebDriver and make use of the driver in the parent class. This would be a less than ideal solution of dependency injection as there would be a direct relationship with the driver class and the sub class where is being used. 











