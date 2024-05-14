# What is HTTP / HTTPS?

HTTP (Hypertext Transfer Protocol) is a protocol that facilitates communication between a client (such as a web browser) and a server. HTTPS (Hypertext Transfer Protocol Secure) is the secure version of HTTP, which uses encryption to protect data exchanged between the client and server.

## HTTP Methods

HTTP methods define the actions that can be performed on resources on the server. The main methods are:

### GET
The GET method is used to request data from a server. It retrieves information such as HTML files, images, or other resources.
#### Example
When you want to retrieve all posts from Twitter, a GET request is made to the server.

### POST
The POST method is used to send data to the server, typically to create new resources or submit data for processing.
#### Example
When you add a new user to a database, a POST request is sent to the server with the user information.

### PUT
The PUT method is used to update existing resources on the server. It replaces the current representation of the target resource with the uploaded content.
#### Example
When you edit an existing tweet, a PUT request is made to update the tweet on the server.

### DELETE
The DELETE method is used to remove resources from the server.
#### Example
When you delete a user or a tweet, a DELETE request is sent to the server to remove the specified resource.

## Server Response

When a server responds to an HTTP request, it provides two main components:

- **HTTP Status Codes:** These codes indicate the result of the request, such as `200 OK` for a successful request or `404 Not Found` for a resource that cannot be found.
- **Data:** The actual content requested, such as HTML pages, JSON data, images, etc.

## Difference Between HTTP and HTTPS

HTTP transmits data in plain text, making it vulnerable to interception by malicious actors. Data can be sent via:

- **Query Strings:** When a form with the GET method is submitted, the data is appended to the URL. For example: `example.com?password=secret&userActive=yes`
- **Body Requests:** When the POST method is used, the data is included in the body of the request, but still visible in transit if not encrypted.

HTTPS, on the other hand, encrypts the data before transmission using SSL/TLS (Secure Sockets Layer/Transport Layer Security), ensuring that the data cannot be easily intercepted or tampered with. This is particularly important for sensitive information like passwords, personal data, and payment details.
