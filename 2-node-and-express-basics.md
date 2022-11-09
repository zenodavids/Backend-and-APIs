## Start a Working Express Server

In Express, routes takes the following structure:

```javascript
app.HttpMETHOD(PATH, HANDLER);
```

- _HttpMETHOD_ is an http method in lowercase(i.e; get, post, put etc).
- _PATH_ is a path on the server (it can be a string, or even a regular expression).
- _HANDLER_ is a function that Express calls when the route is matched.
  Handlers take the form

  ```javascript
  function(req, res) {...}
  ```

  where req is the request object, and res is the response object

to serve just a string, we use;

```javascript
res.send("Hello string");
```

###### ###### task 1

Use the app.get() method to serve the string "Hello Express" to GET requests matching the / (root) path.

```javascript
app.get("/", function (req, res) {
  res.send("Hello Express");
});
```

## Serve an HTML File

respond to requests with a file using the res.sendFile(path)
this simply displays the content of your html file.

```javascript
const absolutePath = `${__dirname} + relativePath/file.fileExtension`;
res.sendFile(absolutePath);
```

###### task 2

Send the _/views/index.html_ file as a response to GET requests to the / path.

```javascript
app.get("/", function (req, res) {
  const absolutePath = `${__dirname}/views/index.html`;
  res.sendFile(absolutePath);
});
```

## Serve Static Assets(stylesheets, scripts, images)

to achieve this, we have to use a _middleware Functionality_;

```javascript
express.static(path);
```

here, where the **path** parameter is the absolute path of the folder containing the assets.

#### middleware

these are functions that intercept route handlers.
middleware can be mounted using;

```javascript
app.use(path, middlewareFunction);
```

The first path argument is optional.
If you don’t pass it, the middleware will be executed for all requests.

###### task 3

Mount the express.static() middleware to the path /public with app.use().
The absolute path to the assets folder is **\_\_dirname + /public.**

```javascript
// All the Assets
app.use(express.static(__dirname + "/public"));

// Assets at the /public route
app.use("/public", express.static(__dirname + "/public"));
```

## Serve JSON on a Specific Route

, This method,

```javascript
res.json();
```

closes the request-response loop, returning the data.
A valid object has the following structure; .

```json
{ "key": "data" }
```

###### task 4

Serve the object {"message": "Hello json"} as a response, in JSON format, to GET requests to the /json route.

```javascript
app.get("/json", function (req, res) {
  res.json({ message: "Hello json" });
});
```

## Use the .env File

- the env file must always be in your root directory
- in the .env file, follow the below convention;

###### the variable names are all uppercase, with words separated by an underscore.

```s
VAR_NAME=value;
```

- access the .env files with ;

```javascript
process.env.VAR_NAME;
```

###### task 5

Create a .env file in the root of your project directory, and store the variable MESSAGE_STYLE=uppercase in it.
Then, in the /json GET route handler you created in the last challenge access process.env.MESSAGE_STYLE and transform the response object's message to uppercase if the variable equals uppercase.
The response object should either be {"message": "Hello json"}

###### in the .env file

```javascript
MESSAGE_STYLE = "uppercase";
```

###### if you're using replit

key = MESSAGE_STYLE
value = uppercase

###### in the app.js

```javascript
app.get("/json", function (req, res) {
  const mySecret = process.env["MESSAGE_STYLE"];
  if (mySecret == "uppercase") {
    res.json({ message: "HELLO JSON" });
  } else {
    res.json({ message: "Hello json" });
  }
});
```

## Implement a Root-Level Request Logger Middleware

Middleware functions are functions that take 3 arguments:

- the request object,
- the response object and
- the next function(next())

If the first two arguments don’t send the response when they are done,
they start the execution of the next function in the stack. This triggers calling the 3rd argument, next().

###### task 6

Build a simple logger.
For every request, it should log to the console a string taking the following format: method path - ip.
An example would look like this: GET /json - ::ffff:127.0.0.1.
Note that there is a space between method and path and that the dash separating path and ip is surrounded by a space on both sides.

```javascript
app.use(function middleware(req, res, next) {
  let string = req.method + " " + req.path + " - " + req.ip;
  console.log(string);
  next();
});
```
