# HTTP Server in Python

The Python standard library includes a module for implementing HTTP
servers called `http.server`. You can find its documentation
[here][http.server doc].

[http.server doc]: https://docs.python.org/3/library/http.server.html

## HTTPServer

The [`HTTPServer`][] class, which inherit from the [`TCPServer`][] super
class, allows us to create a server that listens at the HTTP socket, and
dispatches requests to a handler class.

[`HTTPServer`]: https://docs.python.org/3/library/http.server.html#http.server.HTTPServer
[`TCPServer`]: https://docs.python.org/3/library/socketserver.html#socketserver.TCPServer

`HTTPServer` takes at least 2 arguments: a tuple with the address
(string) and port (integer) to listen to for requests, and the class that
will handle requests:

```python
from http.server import HTTPServer, SimpleHTTPRequestHandler

address = ("localhost", 8080)
handler_class = SimpleHTTPRequestHandler
server = HTTPServer(address, handler_class)

print(
    f"Server listening at http://{address[0]}:{address[1]} ...\n"
    "Press CTRL + C to stop."
)
server.serve_forever()
```

The example above creates and starts a server that listens for requests
at the "localhost:8080" address. The requests are handled by the
`SimpleHTTPRequestHandler` class, which is part of the `http.server`
standard module. This class serves files from the current directory,
directly mapping the directory structure to HTTP requests. For instance,
if the server receives a request with the URL "/", il will look for an
"index.html" file in the working director. If it receives a request with
the URL "/about", it will look for an "index.html" file inside the about
subdirectory.

## BaseRequestHandler

`SimpleHTTPRequestHandler` is predefined as part of the standard
library, but Python allows us to define our own handler class as well.

To do so, we must subclass [`BaseRequestHandler`][], which defines a
common interface for all handler classes. Subclassing
`BaseRequestHandler` allows our handler class to inherit useful
attributes and methods, such as `path`, `wfile` and `send_response()`.

[`BaseRequestHandler`]: https://docs.python.org/3/library/socketserver.html#socketserver.BaseRequestHandler

Below is a simple handler class that responds to requests whose URL path
is "/", but sends back a 404 response to clients making requests to other
paths. Note that a new instance is created for each request.

```python
from http.server import BaseHTTPRequestHandler

class Handler(BaseHTTPRequestHandler):
    def do_GET(self):
        if self.path == "/":
            self.send_response(200)
            self.end_headers()
            self.wfile.write(b"Homepage\n")
        else:
            self.send_response(404)
            self.end_headers()
            self.wfile.write(b"Page not found\n")
```

Let's break the code down to better understand what it does:

-   The `do_GET()` method is used to create responses for requests of
    type GET. It gets called automatically if a GET request is made to
    the server. Similar methods can be defined for POST, DELETE, and so
    forth.
-   The `path` instance variable is assigned to the request's URL path.
    We use it to decide how to respond to specific requests depending on
    their URL.
-   The `send_response()` method adds an [HTTP response status code][]
    to the headers.
-   The `self.end_headers()` method indicates the end of the HTTP
    headers in the response.
-   The `wfile` instance variable contains the output stream for writing
    a response back to the client. We use its `write` method, which
    takes a bytes-like object as argument, to write the response's body.

[HTTP response status code]: https://developer.mozilla.org/en-US/docs/Web/HTTP/Status
