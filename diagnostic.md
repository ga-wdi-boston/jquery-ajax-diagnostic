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
curl --include --request GET "http://www.example.com/donuts"
```

Write an AJAX request to retrieve a list of all donuts on the server.

```js
let getDonuts = (response, error, allDonuts) {
  console.log('Start Request')
  $.ajax({
    method: 'GET',
    url: 'http://www.example.com/donuts'
  })


  console.log('Request queued');
}
```

## Request a Single Resource

Now, we want to get a single donut from the server. Write the `curl` request
you'd use to retrieve a single donut, using whatever ID you'd like.

```sh
curl --include --request GET "http://www.example.com/donuts/$donut"
```

Write an AJAX request to retrieve a single donut from the server.

```js
let getDonut = (response, error, allDonuts) {
  console.log('Start Request')
  $.ajax({
    method: 'GET',
    url: 'http://www.example.com/donuts/' + donut,
  })


  console.log('Request queued');
}
```

## Delete a Single Resource

Write the `curl` request you'd use to delete a single donut, using whatever ID
you'd like.

```sh
curl --include --request DELETE "http://www.example.com/donuts/$donut"
```

Write an AJAX request to delete a single donut from the server.

```js
let deleteDonut = (response, error, donut) => {
  $.ajax({
    method: 'DELETE',
    url: 'http://www.example.com/donuts/$donut',
  }).response(response).error(error);

};
```

## Create a Single Resource

Write the `curl` request you'd use to create a single donut. Use the following
data in JSON format.

```json
curl --include --request POST "http://www.example.com/donuts/" \
  --header "Content-Type: application/json" \
  --data ' {
    "donuts": {
  "name": "French Cruller",
  "price": "$0.99"
  }
}'
```

```sh
# your answer here
```

Write an AJAX request to create a single donut on the server using JSON.

```js
let createDonut = (response, error, donut) => {
  $.ajax({
    method: 'POST',
    url: 'http://www.example.com/donuts/$donut',
  }).response(response).error(error);

};
```

## Change a Single Resource

We don't want to sell French Crullers anymore. We've got a new German supplier,
so we need to change the name of the Cruller in our database. It has an ID of
`42`.

Write the `curl` request you'd use to change the donut. We'll send the following
JSON.

```json


/*//curl --include --request http://www.example.com/donuts/$donut \
  --data-urlencode "donut[name]=$NAME" \
  --data-urlencode "donut[price]=$PRICE"

  curl --include --request POST http://www.example.com/donuts/$donut \
    --header "Content-Type: application/json" \
    --data '{
      "book": {
        "title": "Im a new book",
        "author": "Jason Weeks"
      }
    }'*/





{
  "name": "Krüller"
}
```

```sh
# your answer here
```

Write an AJAX request to change the donut on the server using JSON.

```js
let changeDonut = (response, error, donut) => {
  $.ajax({
    method: 'PATCH',
    url: 'http://www.example.com/donuts/$donut' + donut,
  }).response(response).error(error);

};
```
