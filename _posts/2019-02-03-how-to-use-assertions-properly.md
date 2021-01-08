---
layout: post
title:  "How to use your assertions properly?"
description: "Discussion about proper use of assertions"
author: philip
categories: [ Selenium]
image: assets/images/assertions.jpg
tags: [automation, featured]
---

If your automation test doesn't contain assertions there is no point in running it. It is just a dud. 

> So, how many assertions should you use in your tests? Should each of the important test steps should contain an assertion? If you have test steps and action methods or page object methods where should you put your assertions? 

Let's say you are writing an automation test to verify a salary calculator. It counts the total days you worked for each month and as per your pay grade calculates your salary and gives an amount as output. 

The objective your test is to find the total salary amount given the dates you worked as the input to the program. You name the test as something like `'Customer service agent salary should be grade 2'`. As the first step of your test, you need to login to the program. It is tempting to include an assertion to verify the details soon after login. There is a welcome message in the application that says something like `'Wecome back John Smith'`. You put an assertion step to verify the welcome message to confirm that system identifies you correctly. Then you proceed with writing the rest of the automation script and include another assertion in the end to verify the correct salary amount. 

The salary calculator though sounds a bit simple does a lot of things. It calculates the allowances, holiday pay, leave etc.. and later on you write around 100 automation tests. Some automation tests are complex and involves logging out and logging in again. The assertion we added for the welcome message got included with all the tests as login is a common step for all tests. 

One day, some one pointed out, to add a full stop after the welcome message. The developer did a quick change and it may not even gets communicated with the QA team as this is perceived to be a very minor change without any impact. 

The next day, automation tests run and you get 100 failures. You analyse the result and find the cause and confirms with the developer or product owner about the change. Since you have written a properly structured automation script, you need to make change only at one place and starts to run the tests again. To your surprise, there were a few other test failures as some other changes crept into the code along with the simple full stop change. Between the first test run and second, you lost a few hours and the critical failures you should have noticed with the first test run got masked with an unnecessary welcome message assertion included with all tests. 

* So, your tests should only assert the objective the test. If you are verifying the total salary amount, verify that only. Do not include verifications for other personal details. If you are verifying the leave allowance, verify that only. When the test fails, it should clearly communicate failure from its name itself. When your `'Customer service agent salary should be grade 2'` test fails, you should be able to tell that the application did not calculate the salary correctly without even looking at the error message. 

* If you have a properly structured automation suite, you will have test methods and action methods or page object methods. So where should you add the assertions? Your assertions should go in test steps only. Though it may seem tempting to add assertions in page object methods or action methods, later on it will become counter-intuitive. You should be able to use your action methods or page objects methods without worrying about an included assertion call that could cause a failure. So assertions should always go with the test step methods only. 

* As per the same argument, the action methods or page object methods, should not be aware about data as well. Data should always be supplied from test steps or methods. This would make your action methods ultra flexible and re-usable across different tests. 



