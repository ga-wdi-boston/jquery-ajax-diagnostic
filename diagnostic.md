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
curl --include --request GET 'http://www.example.com/donuts/'
```

Write an AJAX request to retrieve a list of all donuts on the server.

```js
let getDonuts = function (event){
  event.preventDefault();
  libraryApi.index()
    .done(ui.logResponseBody)
    .fail(ui.logRequestError);
};
```

## Request a Single Resource

Now, we want to get a single donut from the server. Write the `curl` request
you'd use to retrieve a single donut, using whatever ID you'd like.

```sh
curl --include --request GET 'http://www.example.com/donuts/10'
```

Write an AJAX request to retrieve a single donut from the server.

```js
let getDonut = = function (event){
  event.preventDefault();
  let donutId = $(event.target).find('[name="donut[id]"]').val();

  if (donutId.length === 0) {
    libraryApi.index()
      .done(ui.logResponseBody)
      .fail(ui.logRequestError);
  } else {
    libraryApi.show(event.target)
      .done(ui.logResponseBody)
      .fail(ui.logRequestError);
  }
};
```

## Delete a Single Resource

Write the `curl` request you'd use to delete a single donut, using whatever ID
you'd like.

```sh
curl --include --request DELETE 'http://www.example.com/donuts/10'
```

Write an AJAX request to delete a single donut from the server.

```js
let deleteDonut = function (event){
  event.preventDefault();
  libraryApi.destroy(event.target)
    .done(ui.logResponseBody)
    .fail(ui.logRequestError);
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
curl --include --request "POST" "http://www.example.com/donuts/" \
  --header "Content-Type: application/json" \
  --data $'{
    "donut": {
      "name": $NAME,
      "price": $PRICE
    }
  }'
```

Write an AJAX request to create a single donut on the server using JSON. Please
do not use `data = getFormFields(form)` instead write out the data object.

```js
let createDonut = function (event) {
  event.preventDefault();
  libraryApi.create(event.target)
    .done(ui.logResponseBody)
    .fail(ui.logRequestError);
};
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
curl --include --request PATCH 'http://www.example.com/donuts/10' \
  --header "Content-Type: application/json" \
  --data $'{
    "donut": {
      "name": $NAME,
      "price": $PRICE
    }
  }'
```

Write an AJAX request to change the donut on the server using JSON.

```js
let changeDonut = function (event) {
  event.preventDefault();
  libraryApi.update(event.target)
    .done(ui.logResponseBody)
    .fail(ui.logRequestError);
};
```
