# Enumeration

The **Enumeration** phase, on the other hand, refers to the process of gatherting detailed information about the services and applications identified in the reconnaissance phase. This may include analyzing open services, identifying users and users groups, file and directory permissions, and searching potential vulnerabilities in the services and applications. **Enumeration** is an important phase for identifying potential attack vectors and planning for the following phases of the pentesting.

Here are some tips for enumeration:

### HTTP / HTTPS

What we have to know before we can enumerate an HTTP / HTTPS Server:

| Example             | Description                       |
| ------------------- | --------------------------------- |
| http(s)://          | Protocol that is being used       |
| domain.com          | Host, it can be an IP or a domain |
| :80, :8080          | Port that is being used to access |
| /index.php,html,etc | File that is being accessed       |
| ?file=welcome.php   | Parameter inside the URL          |
