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

Write the `curl` request you'd use to retrieve a list of **all donuts** on the
server.

```sh
curl --include --request GET http://www.example.com:portNumber/donuts
```

Write an AJAX request to retrieve a list of **all donuts** on the server.

```js
let getDonuts = $.ajax({
    url: http://www.example.com:portNumber + '/donuts',
    method: 'GET',
    success: function (data) {
      console.log('Success function inside show API')
    }
  })
```

## Request a Single Resource

Now, we want to get a **single donut** from the server. Write the `curl` request
you'd use to retrieve a **single donut**, using whatever ID you'd like.

```sh
curl --include --request GET http://www.example.com:9999/donuts/3
```

Write an AJAX request to retrieve a **single donut** from the server.

```js
let getDonut = $.ajax({
    url: http://www.example.com:portNumber + '/donuts/1',
    method: 'GET'
  });
```

## Delete a Single Resource

Write the `curl` request you'd use to delete a single donut, using whatever
ID you'd like.

```sh
curl --include --request DELETE http://www.example.com:9999/donuts/3
```

Write an AJAX request to delete a single donut from the server.

```js
let portNumber  = 4647
let deleteDonut = $.ajax({
    url: http://www.example.com:portNumber + '/donuts/3',
    method: 'DELETE',
    success: function (data) {
      console.log('Success function inside show API')
    }
  });
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

curl "http://www.example.com:9999/donuts" \
  --include \
  --request POST \
  --header "Content-Type: application/json"
  --data {
    "name": "French Cruller",
    "price": "$0.99"
  }
```

Write an AJAX request to create a single donut on the server using JSON. Please
do not use `data = getFormFields(form)` instead write out the data object.

```js
let portNumber =9999
let createDonut = $.ajax({
    url: http://www.example.com:portNumber + '/donuts',
    method: 'POST',
    data: {
      "name": "French Cruller",
      "price": "$0.99"
    }
  });
```

## Change a Single Resource

We don't want to sell French Crullers anymore. We've got a new German supplier,
so we need to change the name of the Cruller in our database. It has an ID of
`42`.

Write the `curl` request you'd use to change the donut. We'll send the following
JSON. Please do not use `data = getFormFields(form)` instead write out the data
object.

```json
{
  "name": "Krüller"
}
```

```sh
let portNumber = 9999
curl "http://www.example.com:portNumber/donuts/42" \
  --include \
  --request PATCH \
  --header "Content-Type: application/json"
  --data {
    "name": "Krüller",
  }
```

Write an AJAX request to change the donut on the server using JSON.

```js
let portNumber  = 9999
let changeDonut = $.ajax({
    url: http://www.example.com:portNumber/donuts/42,
    method: 'PATCH',
    data: {
      "name": "Krüller",
    }
  });
```
