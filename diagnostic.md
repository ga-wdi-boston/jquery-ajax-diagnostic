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
curl --request GET http://10.13.105.206:3000/items
```

Write an AJAX request to retrieve a list of all donuts on the server.

```js
let getDonuts = function(){
$.ajax({                                    // $ is jquery, exercute ajax in ().  everything inside is an object literal
url: 'http://10.13.105.206:3000/items',     // a key is url, retrieve a list of items
type: 'GET'                                 // tell ajax to get
})                                          // ajax takes these info and use it

.done(logResponseBody)                      // register that function when you hear done
.fail(logRequestError);                     // register that function when you hear fail
};
```

## Request a Single Resource

Now, we want to get a single donut from the server. Write the `curl` request
you'd use to retrieve a single donut, using whatever ID you'd like.

```sh
curl --request GET http://10.13.105.206:3000/
```

Write an AJAX request to retrieve a single donut from the server.

```js
let getDonut = function(){
$.ajax({                                    // $ is jquery, exercute ajax in ().  everything inside is an object literal
url: 'http://10.13.105.206:3000/items/<item#id>',          // a key is url, retrieve an items
type: 'GET'                                 // tell ajax to get
})                                          // ajax takes these info and use it

.done(logResponseBody)                      // register that function when you hear done
.fail(logRequestError);                     // register that function when you hear fail
};
```

## Delete a Single Resource

Write the `curl` request you'd use to delete a single donut, using whatever ID
you'd like.

```sh
curl --request DELETE http://10.13.105.206:3000/items/2005
```

Write an AJAX request to delete a single donut from the server.

```js
let deleteDonut = function(){
$.ajax({                                    // $ is jquery, exercute ajax in ().  everything inside is an object literal
url: 'http://10.13.105.206:3000/items/<item#id>',          // a key is url, retrieve an items
type: 'DELETE'                                 // tell ajax to get
})                                          // ajax takes these info and use it

.done(logResponseBody)                      // register that function when you hear done
.fail(logRequestError);                     // register that function when you hear fail
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
curl --request POST http://localhost3000/items --header "Content-Type: application/json" --data '{ "content": "DDOS the server", "done": false, "list":1}
```

Write an AJAX request to create a single donut on the server using JSON.

```js
let createDonut = let createItem =  function(event) {
  event.preventDefault();
  $.ajax({
    url: 'http://localhost:3000/items',
    type: 'POST',
    data: {
      'content': $(event.target).find('#content').val(),
      'done': $(event.target).find('#done').val(),
      'list_id': $(event.target).find('#list-id').val()
    }
  })
  .done(logResponseBody)
  .fail(logRequestError);
};
```

Now, rewrite your AJAX request to use FormData. Assume you have already targeted
the correct HTML form before registering your AJAX function with the form.

```js
let createDonut = new FormData(event.target);
  $.ajax({
    url: 'http://localhost:3000/items' + itemId, // make this a variable
    type: 'PATCH',
    contentType: false,
    processData: false,
    data: item
  })
  .done(logResponseBody)
  .fail(logRequestError)
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
# this is my comment
curl --request PATCH http://10.13.105.206:3000/items/1 \
 --header "Content-Type: application/json" \
 --data '{
   "done": true
 }'
```

Write an AJAX request to change the donut on the server using JSON.

```js
let changeDonut = function(event) {
  event.preventDefault();
  // data stores here
  let itemIdInput = $(event.target).find('[name="name_id"]');
  // pull the value out // .val() get value
  //let itemId = $(event.target).find('[name="item_id"]').val(); // event.target is the form, access jquery method. [name=], pseudo id selector
  let item = new FormData(event.target);
  $.ajax({
    url: 'http://localhost:3000/items' + itemId, // make this a variable
    type: 'PATCH',
    contentType: false,
    processData: false,
    data: item
  })
  .done(logResponseBody)
  .fail(logRequestError);
  // .val("") set value
  //$(event.target).find('[name="item_id"]').val("");

  itemIdInput.val('');
};
```

Now, rewrite your AJAX request to use FormData. Assume you have already targeted
the correct HTML form before registering your AJAX function with the form.

```js
let changeDonut = /* your answer here */;
```
