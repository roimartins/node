### Reference document

https://dev.to/kyrelldixon/how-to-setup-an-express-js-server-in-node-js-56hp

#### Creating REST API Endpoints

The first endpoint we'll create will handle a GET request. 
It have been created the var url_pre to include the path created in NGINX proxy

```js 

const express = require ("express");
const app = express();
const PORT = 3000;
const url_pre = '/react_test';

app.get( url_pre + "/hello", (req, res) =>  {
        res.send ( "Hello world") ;
});

app.listen (PORT, () => {
        console.log("Server is listening on Port: 3000") ;
});



```

First we have app.get("/hello", ...) which tells the server that we want to be able to handle a GET request to the /hello endpoint.

Following the endpoint is (req, res) => {...} which is an ES6 arrow function that takes two parameters req and res.

The first parameter req is a variable that stores all the information for the incoming request from the client. The server response functions are stored in the res parameter.

In this case we are using res.send to respond with the string "Hello world".

The GET route for the "hello" endpoint is currently sending down the string "Hello world", but we could have it send pretty much any document containing text--which is all a JSON or HTML file really is.

A browser is great for quickly testing our GET endpoints, but if you need to test any other type of request like a POST or DELETE, you will need a different method entirely. This next method will show you how to test your endpoints entirely from the command line using cURL.

### **Test any API endpoints from the command line with cURL**
Sometimes you want to quickly test your API endpoint without having to leave your code editor. If you are working with Visual Studio Code, then you can test your API endpoints without needing to open up another app. (If not, you can open up the terminal and still take advantage of this method.)

To test your endpoints with cURL, go to your command line and type:

```
curl https://azscgislnxdev02/react_test/hello
```

### Reduce development errors with nodemon

nytime you make changes to your server you have to stop and restart the server to be able to test those changes. Forgetting to restart the server can lead to hours of frustration and doubt because you think your code isn't working when in reality the server just hasn't loaded the changes.

If you haven't felt this struggle you are one of the lucky few. This tip will make it so you never encounter it. The solution is to install an npm package called nodemon.

With nodemon, you will never have to manually restart your server. It runs in the background and watches all your files for changes. When it detects one, it will automatically restart the server so you can focus on writing code.

To get started you will need to install it:

```
npm i --save-dev nodemon 
```

Here you use the --save-dev or alternatively the -D flag to add nodemon to you devDependencies in the package.json file.

We added it to the devDependicies since this is just a convenient way to run the server to make development easier and isn't required to have a working application.

To use nodemon to run the server, first you want to add a "start" script to the package.json in the "scripts" object:

```js 
"scripts": {
  "start": "nodemon index.js",
  "test": "echo \"Error: no test specified\" && exit 1"
},
```
