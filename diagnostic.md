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
curl --include --request GET "http://example.com/donuts"
```

Write an AJAX request to retrieve a list of all donuts on the server.

```js
let getDonuts = (success, fail) => {
  console.log('Started request');
  $.ajax({
    method: 'GET',
    url: 'http://example.com/donuts'
  })
  .done(success)
  .fail(fail);
  console.log('Request queued');

};
```

## Request a Single Resource

Now, we want to get a single donut from the server. Write the `curl` request
you'd use to retrieve a single donut, using whatever ID you'd like.

```sh
curl --include --request GET "http://example.com/donuts/7"
```

Write an AJAX request to retrieve a single donut from the server.

```js
let getDonut = (donutId, success, fail) => {
  console.log('Started request');
  $.ajax({
    method: 'GET',
    url: 'http://example.com/donuts' + donutId,
  })
  .done(success)
  .fail(fail);
  console.log('Request queued');

};
```

## Delete a Single Resource

Write the `curl` request you'd use to delete a single donut, using whatever ID
you'd like.

```sh
curl --include --request DELETE "http://example.com/donuts/7"
```

Write an AJAX request to delete a single donut from the server.

```js
let getDonut = (donutId, success, fail) => {
  console.log('Started request');
  $.ajax({
    method: 'DELETE',
    url: 'http://example.com/donuts' + donutId,
  })
  .done(success)
  .fail(fail);
  console.log('Request queued');

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
curl --include --request POST http://example.com/donuts \
  --header "Content-Type: application/json" \
  --data '{
    "donut": {
      "name": "French Cruller",
      "price": "0.99"
    }
  }'
```

Write an AJAX request to create a single donut on the server using JSON.

```js
let createDonut = (success, fail, id) => {
  console.log('Start request');
  if ( {
  $.ajax({
    method: 'POST',
    url: 'http://example.com/donuts' + id,
    processData: false,
    data: form
  })
  .done(success)
  .fail(fail);
  console.log('Request queued');
}
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
curl --include --request PATCH http://example.com/donuts/42 \
  --header "Content-Type: application/json" \
  --data '{
    "donut": {
    "name": "Krüller"
    }
  }'
```

Write an AJAX request to change the donut on the server using JSON.

```js
let changeDonut = (success, fail, id) => {
  console.log('Start request');
  if ( {
  $.ajax({
    method: 'PATCH',
    url: 'http://example.com/donuts' + id,
    processData: false,
    data: form
  })
  .done(success)
  .fail(fail);
  console.log('Request queued');
}
};
```
