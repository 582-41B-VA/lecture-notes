# REST

REST stands for Representational State Transfer. It is a set of design
principles for making network communication more scalable and flexible.
Roy T. Fielding first coined the term REST in 2000, in his PhD
dissertation [Architectural Styles and the Design of Network-based
Software Architectures][Fielding].

[Fielding]: https://ics.uci.edu/~fielding/pubs/dissertation/top.htm

Fielding's dissertation outlines a number of architectural constraints
that a system must satisfy to be considered RESTful. Let's take a look
at them one by one.

## Client-server

A RESTful network must be made up of clients and servers:

-   A server is a computer that has resources of interest.
-   A client is a computer that wants to interact with the resources
    stored on the server.

When you browse the Internet, your computer is acting as a client that
sends HTTP requests to a server in order to access and manipulate
information.

## Stateless

Clients and servers do not need to keep track of each other's state.
When a client is not interacting with the server, the server has no idea
of its existence. The server also does not keep a record of past
requests. Each request is treated as a standalone.

## Uniform interface

Servers and clients need a common language that allows each part to be
modified without breaking the entire system. This is achieved through 4
sub-constraints:

### Identification of resources

Resources must be uniquely identified by a stable identifier that never
changes. A resource could be anything – an HTML document, an image,
information about a particular user, etc. If a resource does get moved
to another identifier, the server should give the client a response
indicating that the request was bad, and give it a link to the new
location of the resource.

The Web uses Uniform Ressource Identifiers (URI) to identify resources,
and the Hypertext Transfer Protocol (HTTP) as its communication
standard. To get a resource stored on a server, a client makes a HTTP
GET request to the URI that identifies that resource. Every time you
type an address into your browser, your browser makes a GET request to
that URI. If it receives a 200 OK response and an HTML document back,
then it renders the page in the window so that you can view it.

### Manipulation of resources through representations

Client manipulates resources through sending representations to the
server. The server has full control of the resources, and is responsible
for making any changes. It takes the request as a suggestion, but still
has ultimate control.

When a website user submits a form, the browser does not tell the server
how to process the data. It merely sends an HTTP POST or PUT request
with the form's content.

### Self-descriptive messages

Messages sent between client and server must contains all the
information needed to understand them. There should not be additional
information in a separate documentation or in another message.

When a user types "http://www.example.com" in the address bar of their
web browser, the browser sends the following HTTP request:

```
GET / HTTP/1.1
Host: www.example.com
```

This message is self-descriptive because it tells the server the HTTP
method (GET) and protocol (HTTP 1.1) that was used.

The server may send back a response like this:

```
HTTP/1.1 200 OK
Content-Type: text/html

<!DOCTYPE html>
<html>
  <head>
    <title>Home Page</title>
  </head>
  </body>
    <h1>Hello World!</h1>
  </body>
</html>
```

This message is self-descriptive because it tells the client how it needs
to interpret the message body, by indicating that Content-type is
text/html. The client has everything it needs in this single message to
handle it appropriately.

### Hypermedia

Servers should be sending only hypermedia to clients. Hypermedia is data
sent from the server to the client that contains information about what
the client can do next – in other words, what further requests it can
make.

HTML is a type of hypermedia. Anchor elements, for example, tell clients
that they can make GET requests to a specific URL. Similarly, image
embed elements tells clients they can make GET requests to display
images.

## Resources

- Lauren Long. [What RESTful actually means](https://codewords.recurse.com/issues/five/what-restful-actually-means).
- Codecademy. [What is REST?](https://www.codecademy.com/article/what-is-rest).