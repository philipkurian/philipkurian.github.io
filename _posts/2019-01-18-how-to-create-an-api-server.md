---
layout: post
title:  "How to create an API server in 30 Seconds"
description: "You can create your own server in thirty seconds"
author: philip
categories: [API]
image: assets/images/apiserverinthirtysec.jpg
tags: [automation, featured]
---

If you need an API server for your test or development purpose, 'json-server' is an excellent option to get your mock data uploaded and available in no time. 

Here I am listing the few simple steps to get it done. I assume you have installed node package manager (npm) in your computer.

Create a folder named 'API Server' or whatever name you wish to give.
Open command prompt and type the following command and then press enter
```
npm install -g json-server
```

Create a file in the json-server folder named 'db.json' and in it create a json array 

```json
{ "people" : [ {"id": 1, "First Name": "Harry", "Last Name": "Potter"}] }
```

Open command prompt from the folder and type **'json-server db.json'**
Your server is up and running!

You can access it with the URL `"http://localhost:3000"` and the data with `http://localhost:3000/people/1` etc. You can add, delete and update the data using tools like Postman or through your Automation Scripts.

You can save a snapshot of the current database by typing **'s'** and press enter in current session in the terminal. Press  `Control+C`  to end the session.

If you think the current data is not enough, there is another quick option using 'faker js' to create some fake data. Follow the steps below

Create a file called **'generate-data.js'** in the folder.
Open the terminal from the folder and install faker and lodash with the command

```
npm install faker lodash
```

Remember, you have to install the module in the server folder itself.
Type the following code in 'generate-data.js' file and save it

```javascript
module.exports = function() {
    var faker = require("faker");
    var _=require("lodash");
     return {
       people: _.times(100, function(n) {
         return {
             id:n,
             FirstName: faker.name.firstName(),
             LastName: faker.name.lastName(),
             Phone:faker.phone.phoneNumber(), 
             Email:faker.internet.email(),
             avatar: faker.internet.avatar()
           }
       })
     }
}
```


Now open the terminal from the server folder and type the command and then press enter

```
json-server generate-data.js
``` 

A ton of data is ready for your testing! You can be more creative if you refer to the faker.js documentation and know how to autogenerate the data with a lot of other options described there.

Note: Always remember to initialize the server from the terminal before you start using it. Open the terminal from the server folder and type 'json-server db.json' and you are ready to go.