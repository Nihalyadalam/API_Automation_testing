# API_Automation_testing
Testing a Book API and automating the functionality using Postman   

# Running the Automated Books API #

- Install postman on your local machine.
- Install NPM and node.js on your local machine.
- Open Node.js command prompt and execute ``` $ npm install -g newman ```
- Load the json files using the command ```newman run Books_API_postman_collection.json --globals workspace.postman_globals.json``` to generate the test report containing all the Endpoints (jobs) of an API.


![image](https://user-images.githubusercontent.com/18449111/151284388-6612e9c6-2410-47f8-9458-c7438b258217.png)

# Books API #

This API allows you to reserve a book.

The API is available at `https://simple-books-api.glitch.me`

## Endpoints ##

### Status ###

GET `/status`

Returns the status of the API.

### List of books ###

GET `/books`

Returns a list of books.

Optional query parameters:

- type: fiction or non-fiction
- limit: a number between 1 and 20.


### Get a single book ###

GET `/books/:bookId`

Retrieve detailed information about a book.


### Submit an order ###

POST `/orders`

Allows you to submit a new order. Requires authentication.

The request body needs to be in JSON format and include the following properties:

 - `bookId` - Integer - Required
 - `customerName` - String - Required

Example
```
POST /orders/
Authorization: Bearer <YOUR TOKEN>

{
  "bookId": 1,
  "customerName": "John"
}
```

The response body will contain the order Id.

### Get all orders ###

GET `/orders`

Allows you to view all orders. Requires authentication.

### Get an order ###

GET `/orders/:orderId`

Allows you to view an existing order. Requires authentication.

### Update an order ###

PATCH `/orders/:orderId`

Update an existing order. Requires authentication.

The request body needs to be in JSON format and allows you to update the following properties:

 - `customerName` - String

 Example
```
PATCH /orders/PF6MflPDcuhWobZcgmJy5
Authorization: Bearer <YOUR TOKEN>

{
  "customerName": "John"
}
```

### Delete an order ###

DELETE `/orders/:orderId`

Delete an existing order. Requires authentication.

The request body needs to be empty.

 Example
```
DELETE /orders/PF6MflPDcuhWobZcgmJy5
Authorization: Bearer <YOUR TOKEN>
```

## API Authentication ##

To submit or view an order, you need to register your API client.

POST `/api-clients/`

The request body needs to be in JSON format and include the following properties:

 - `clientName` - String
 - `clientEmail` - String

 Example

 ```
 {
    "clientName": "Valentin",
    "clientEmail": "valentin@example.com"
}
 ```

The response body will contain the access token.

**Possible errors**

Status code 409 - "API client already registered." Try changing the values for `clientEmail` and `clientName` to something else.





