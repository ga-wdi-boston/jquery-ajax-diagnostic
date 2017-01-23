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
curl --include --request GET 'http://www.example.com/donuts/'
```

Write an AJAX request to retrieve a list of **all donuts** on the server.

```js
//I think you still need to get the ID's of every indiviudal donut if you want a list of all the donuts...

let getDonuts = function () {
  return $.ajax({
    url: http://www.example.com/donuts,
    method: 'GET',
  });
};
```

## Request a Single Resource

Now, we want to get a **single donut** from the server. Write the `curl` request
you'd use to retrieve a **single donut**, using whatever ID you'd like.

//

```sh
//Not sure about this curl request... Does the URL know what we mean by // //singleDonut yet?

curl --include --request GET 'http://www.example.com/donuts/singleDonut/'

```

Write an AJAX request to retrieve a **single donut** from the server.

```js
//this will be the same as getting the list of donuts, except we are now
//tracking the ID's of the indiviudal donuts as parameters.
let getDonut = function (singleDonut) {
  return $.ajax({
    url: http://www.example.com/donuts + singleDonut,
    method: 'GET',
  });
};
```

## Delete a Single Resource

Write the `curl` request you'd use to delete a single donut, using whatever
ID you'd like.

```sh
curl --include --request DELETE 'http://www.example.com/donuts/singleDonut/'
```

Write an AJAX request to delete a single donut from the server.

```js
let deleteDonut = function (singleDonut) {
  return $.ajax({
    url: http://www.example.com/donuts + singleDonut,
    method: 'DELETE',
  });
};;
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
curl --include --request POST http://www.example.com/donuts

--HEADER "Content-Type: application/json"\
--data {
"book": {
  “name”: “French Cruller”,
  “price”: “$9.99”
}
}
```

Write an AJAX request to create a single donut on the server using JSON. Please
do not use `data = getFormFields(form)` instead write out the data object.

```js
// I believe this is mostly the right syntax, but I also think I needed a quote around the curly bracket after the data: --data '{ because it is JSON, which is a string and that is how it is able to be interpeted, but when I do that, everything inside of the strings go red... now just the .99 is red as you can see. I was never getting an error from atom, but It didn't look right, so I am not entirely sure what to make of the situation and will leave off the quote for now.

let createDonut =  function() {
	return $.ajax({
		url: ‘ http://www.example.com/donuts’,
		method: ‘POST’,
	data: {
	  “donut” {
		“name”: “Name your donut”,
		“price”: “$0.99”
		}
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
curl --include --request PATCH http://www.example.com/donuts/42” \
	--HEADER "Content-Type: application/json" \
--data {
  “donut”: {
    “name”: “Kruller”,
  }
}
```

Write an AJAX request to change the donut on the server using JSON.

```js
//running out of time!!
let createDonut =  function() {
	return $.ajax({
		url: ‘ http://www.example.com/donuts’,
		method: 'PATCH',
	data: {
    “donut”: {
      “name”: “Kruller”,
    }
	}
});;
```
