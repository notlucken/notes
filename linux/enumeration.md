# Enumeration

The **Enumeration** phase, on the other hand, refers to the process of gatherting detailed information about the services and applications identified in the reconnaissance phase. This may include analyzing open services, identifying users and users groups, file and directory permissions, and searching potential vulnerabilities in the services and applications. **Enumeration** is an important phase for identifying potential attack vectors and planning for the following phases of the pentesting.

Here are some tips for enumeration:

## HTTP / HTTPS

What we have to know before we can enumerate an HTTP / HTTPS Server:

| Example             | Description                       |
| ------------------- | --------------------------------- |
| http(s)://          | Protocol that is being used       |
| domain.com          | Host, it can be an IP or a domain |
| :80, :8080          | Port that is being used to access |
| /index.php,html,etc | File that is being accessed       |
| ?file=welcome.php   | Parameter inside the URL          |

## Request

### What is a Request

In HTTP/HTTPS, a **request** is a message sent by a client to a server to ask for  a specific action or information. The client can be a web browser, a mobile app, or any other software that communicates with a web server.

The request typically includes the following components:

| Name | Description |
|-------|---------------|
|Request Method| This indicates the HTTP method to be used, such as GET, POST, PUT, DELETE, etc.|
| Request URL | This specifies the URL of the resource that the client wants to access.|
|Request headers| These are optional elements that provide additional information about the request, such as the user agent, accept-language, or authorization.|
| Request body | This is an optional component that contains data sent by the client to the server, such as form data or JSON data.|

When the server receives the request, it processes the request and sends back a response to the client. The response typically includes a status code indicating whether the request was successful or not, as well as any data or information requested by the client.
