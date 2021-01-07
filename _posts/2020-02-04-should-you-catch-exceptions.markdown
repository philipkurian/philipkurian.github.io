---
layout: post
title:  "Should you handle your exceptions with test automation?"
description: "Proper use of exception handling in test automation"
author: philip
categories: [ Testing ]
image: assets/images/10.jpg
---

Should you wrap your test methods in a try catch statement and handle or throw the exceptions? 

You should not. I will tell you why. Consider the example below. 

```java

  public void userLogin(String userName, String password){
    try{
      driver.findElement(By.id("userName")).sendKeys(userName);
      driver.findElement(By.id("password")).sendKeys(password);
      driver.findElement(By.id("submitButton")).click();
    } catch(Exception e){
      e.printStackTrace();
    }
  }

  ```

  The problem here is that the exception can happen with any of the above three driver actions and even though you will get a stack trace of the error printed, your test will continue as nothing happened and fail at the next stage. So the actual failure point will be different and you will get a different error message unless you stop and read the previous error message from the stack trace. 

  Next one is a rethrow of the actual error. Sometimes people do it to add more information. 


  ```java

  public void userLogin(String userName, String password){
    try{
      driver.findElement(By.id("userName")).sendKeys(userName);
      driver.findElement(By.id("password")).sendKeys(password);
      driver.findElement(By.id("submitButton")).click();
    } catch(Exception e){
      e.printStackTrace();
      throw new RunTimeException("Error with userLogin");
    }
  }

``` 

Though this is better than the previous example, you have to look back at the stack trace error message to find the actual cause of failure. Imagine the situation if you decide not to print the stack trace message and you will never find the real error. 

So it is better not to catch the exceptions and let the error be thrown whenever it happens. Your code is not production code. Let if fail when there is an error and that's how automation testing works. 




