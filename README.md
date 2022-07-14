# req.query
- using ? in url.
- It's taken the query parameter after ? in URL and turn it into JSON.
- the following is req.query when URL is " http://localhost:3001/api/animals?name=Erica"
```js
{name: 'Erica}
```
- "?a=111&b=222&c=333" will become:
- req.query is:
```js
{
    a: "111",
    b: "222",
    c: "333"
}
```
- if you repeat the same query name with different values, it will become an array in the JSON.
- "?a=111&b=222&b=333" would become 
- req.query:
```js
{
    a: "111",
    b: ["222", "333"]
}
```

# req.params === the param object needs to be defined in the route path. 
- definiation "<route>/:<parameterName>" URL: "http://localhost:3001/api/animals/1"

## req.query is multifaceted, often combining multiple parameters, 
## whereas req.param is specific to a single property, often intended to retrieve a single record.

# GET requests
- How we make GET requests
    - We make a GET request every time we enter a URL into the browser and press the Enter key to see what will come back in response.

# Express.js process
- When we make any type of request to the server, Express.js will go through a couple of different phases. 
- First, it'll take the URL we made a request to and check to see if it's one of the URL endpoints we've defined. 
- Once it finds a matching route, it then checks to see the method of the request and determines which callback function to execute.

# POST
## req.body
- With POST requests, we can package up data, typically as an object, and send it to the server. 
- The req.body property is where we can access that data on the server side and do something with it.

## risk of Post
- Accepting data from a client can be risky. While we expect to receive the type of data we asked for, there is nothing stopping a user from sending incorrect or malicious data to our server. For this reason, there are validation libraries that ensure (on the server side) that the data meets certain criteria.

- It is also why most APIs require that the user must be authenticated to make a POST request, as an access token provided by an authenticated user will let the server confirm that the person making the request is allowed to.

# REST
- This stands for REpresentational State Transfer

# middleware , app.use()
- This is a method executed by our Express.js server that mounts a function to the server that our requests will pass through before getting to the intended endpoint. 
- The functions we can mount to our server are referred to as middleware.
- To learn more about this method, check out the [Express.js documentation for app.use()](https://expressjs.com/en/4x/api.html#app.use)
- Middleware functions can serve many different purposes. Ultimately they allow us to keep our route endpoint callback functions more readable while letting us reuse functionality across routes to keep our code DRY.
- express.urlencoded({extended: true})
    - is a method built into Express.js. 
    - It takes incoming POST data and converts it to key/value pairings that can be accessed in the req.body object. 
    - The extended: true option set inside the method call informs our server that there may be sub-array data nested in it as well, so it needs to look as deep into the POST data as possible to parse all of the data correctly.
- express.json()
    - takes incoming POST data in the form of JSON and parses it into the req.body JavaScript object.

# Validation
- validating data is a very important part of building an application because it allows our app to look for values in a consistent fashion without any "what if" scenarios.
- We can add as much or as little validation as we want—it's completely up to us how strict we need to be.

# Middleware
- The middleware is a helper funtion works between request and response cycle.

# Route naming patterns
- a route that has the term api in it will deal in transference of JSON data, 
- whereas a more normal-looking endpoint such as /animals should serve an HTML page.