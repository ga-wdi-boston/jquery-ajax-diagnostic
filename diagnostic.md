# jQuery AJAX Diagnostic

Place your answers inside the fenced code-blocks where indicated by comments.

For all responses,  assume you have already defined a `logResponseBody` handler
to output your results to the console on success, and that you have a
`logRequestError` to print any errors that occur to the console if the request
fails.

For all responses, you need to include the proper flags for `curl`. You are
expected to use the appropriate HTTP method, and to ask `curl` to include HTTP
headers in its output.

## Request a Collection Resource

Suppose we have an API serving donuts. We want to get a list of all donuts in
the system. In other words, we want to `GET /donuts`. The hostname of the
machine serving the donuts is `http://www.example.com`.

Write the `curl` request you'd use to retrieve a list of all donuts on the
server.

```sh
curl --request GEt http://www.example.com/donuts```

Write an AJAX request to retrieve a list of all donuts on the server.

```js
let getDonuts = function() {
$.ajax({
  url: 'http://www.example.com/donuts',
  type: 'GET'
})
.done(logResponseBody)
.fail(logRequestError);
};
```

## Request a Single Resource

Now, we want to get a single donut from the server. Write the `curl` request
you'd use to retrieve a single donut, using whatever ID you'd like.

```sh
curl --request GET http://www.example.com/donuts/17
```

Write an AJAX request to retrieve a single donut from the server.

```js
let getDonut = function() {
$.ajax({
  url: 'http://www.example.com/donuts/17',
  type: 'GET'
})
.done(logResponseBody)
.fail(logRequestError);
};
```

## Delete a Single Resource

Write the `curl` request you'd use to delete a single donut, using whatever ID
you'd like.

```sh
curl --request DELETE http://www.example.com/donuts/17
```

Write an AJAX request to delete a single donut from the server.

```js
let getDonut = function() {
$.ajax({
  url: 'http://www.example.com/donuts/17',
  type: 'DELETE'
})
.done(logResponseBody)
.fail(logRequestError);
};
```

## Create a Single Resource

Write the `curl` request you'd use to create a single donut. Use the following
data in JSON format.

```json
{
  "name": "French Cruller",
  "price": "$0.99"
}
```

```sh
curl --request POST http://www.example.com/donuts \
--header "Content-Type: application/json" \
--data '{"name": "French Cruller",
"price": "$0.99"}'
```

Write an AJAX request to create a single donut on the server using JSON.

```js
let createDonut = function() {
  let item = new donut;
$.ajax({
  url: 'http://www.example.com/donuts/',
  type 'POST',
  contentType: false,
  processData: false,
  data: item
})
.done(logResponseBody)
.fail(logRequestError);
};
```

Now, rewrite your AJAX request to use FormData. Assume you have already targeted
the correct HTML form before registering your AJAX function with the form.

```js
let createDonut = function() {
  event.preventDefault();
  let item = new FormData(event.target);
$.ajax({
  url: 'http://www.example.com/donuts',
  type 'POST',
  contentType: false,
  processData: false,
  data: item
})
.done(logResponseBody)
.fail(logRequestError);
};
```

## Change a Single Resource

We don't want to sell French Crullers anymore. We've got a new German supplier,
so we need to change the name of the Cruller in our database. It has an ID of
`42`.

Write the `curl` request you'd use to change the donut. We'll send the following
JSON.

```json
{
  "name": "Krüller"
}
```

```sh
curl --request PATCH http://www.example.com/donuts/42 \
--header "COntent-Type: application/json" \
--data '{"name": "Krüller"}'
```

Write an AJAX request to change the donut on the server using JSON.

```js
let changeDonut =  function() {
  let item ={
    name: "Krüller"
  };
  $.ajax({
    url: 'http://www.example.com/donuts/42',
    type 'PATCH',
    contentType: false,
    processData: false,
    data: item
  })
  .done(logResponseBody)
  .fail(logRequestError);
  };
```

Now, rewrite your AJAX request to use FormData. Assume you have already targeted
the correct HTML form before registering your AJAX function with the form.

```js
let changeDonut = /* your answer here */;
```
