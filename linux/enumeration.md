# Enumeration

## Enumeration

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

### Request

#### What is a Request

In HTTP/HTTPS, a **request** is a message sent by a client to a server to ask for a specific action or information. The client can be a web browser, a mobile app, or any other software that communicates with a web server.

The request typically includes the following components:

<figure><img src="../.gitbook/assets/httpmsg2.png" alt=""><figcaption><p>Request Example</p></figcaption></figure>

| Name            | Description                                                                                                                                   |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| Request Method  | This indicates the HTTP method to be used, such as GET, POST, PUT, DELETE, etc.                                                               |
| Request URL     | This specifies the URL of the resource that the client wants to access.                                                                       |
| Request headers | These are optional elements that provide additional information about the request, such as the user agent, accept-language, or authorization. |
| Request body    | This is an optional component that contains data sent by the client to the server, such as form data or JSON data.                            |

When the server receives the request, it processes the request and sends back a response to the client. The response typically includes a status code indicating whether the request was successful or not, as well as any data or information requested by the client.

### Response

## FTP

FTP (File Transfer Protocol) is a protocol used for transferring files between systems over a network. During a pentest, FTP can be a potential target for attackers or a tool for security testers to identify vulnerabilities.

### vsFTPd

One of the most used FTP Servers on Linux-based OS is **vsFTPd**.

#### Default Configuration location

`/etc/vsftpd.conf`

Some of the default configutarion settings:

| Setting                        | Description                                                                       |
| ------------------------------ | --------------------------------------------------------------------------------- |
| anonymous\_enable=YES          | Anonymous Login is On                                                             |
| anon\_upload\_enable= YES      | Allow anonymous login to upload files                                             |
| anon\_mkdir\_write\_enable=YES | Allows anonymous to create directories                                            |
| no\_anon\_password=YES         | It doesn't ask for a password in an Anonymous login                               |
| anon\_root=/var/ftp            | The anonymous directory                                                           |
| write\_enable=YES              | Allow the usage of FTP commands: STOR, DELE, RNFR, RNTO, MKD, RMD, APPE, and SITE |

Nmap can tell you if there's enable anonymous login:

#### How to login FTP

```bash
root@localhost$ ftp <IP>

> anonymous
> anonymous

230 Login Succesful.
Remote system type is UNIX.
Using binary mode to transfer files.

ftp>
```

Here are some ways that FTP can be relevant to a pentest:

1. Enumeration: FTP servers may be running on the target system and can be enumerated to identify the users, groups, and files available on the server.
2. Authentication: The authentication process used by the FTP server can be tested for vulnerabilities, such as weak passwords, unencrypted transmission of login credentials, or anonymous login access.
3. File transfer: The files transferred over FTP may contain sensitive information, such as login credentials, configuration files, or proprietary information, and can be used by attackers for malicious purposes.
4. Privilege escalation: FTP servers may have misconfigured permissions that allow attackers to escalate their privileges or execute arbitrary commands.
5. Backdoor access: FTP servers can be used as a backdoor to access the target system by uploading and executing malicious files.

During a pentest, testers can use tools such as Nmap, Metasploit, or Hydra to identify and exploit vulnerabilities in FTP servers.
