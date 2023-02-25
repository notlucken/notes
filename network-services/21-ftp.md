# 21 - FTP

FTP (File Transfer Protocol) is a protocol used for transferring files between systems over a network. During a pentest, FTP can be a potential target for attackers or a tool for security testers to identify vulnerabilities.

## How to login FTP

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

1. **Enumeration**: FTP servers may be running on the target system and can be enumerated to identify the users, groups, and files available on the server.
2. **Authentication**: The authentication process used by the FTP server can be tested for vulnerabilities, such as weak passwords, unencrypted transmission of login credentials, or anonymous login access.
3. **File transfer**: The files transferred over FTP may contain sensitive information, such as login credentials, configuration files, or proprietary information, and can be used by attackers for malicious purposes.
4. **Privilege escalation**: FTP servers may have misconfigured permissions that allow attackers to escalate their privileges or execute arbitrary commands.
5. **Backdoor access**: FTP servers can be used as a backdoor to access the target system by uploading and executing malicious files.

During a pentest, testers can use tools such as Nmap, Metasploit, or Hydra to identify and exploit vulnerabilities in FTP servers.

## Download files from FTP

```bash
ftp> get *

wget -m ftp://user:passwd@<IP> # This will download all files from FTP
```

## FTP Useful Commands

* `USER` \<username>
* `PASS` \<passwd>
* `LIST` List files on the current folder
* `APPE /path/file.txt` Indicate to store data received from a passive connection or from a **PORT/ERPT** connection to a file. It will appen the data if the filename exists.
* `STOR /path/file.txt` Like `APPE` but it can overwrite.
* `STOU /path/file.txt` Like`APPE` but it won't overwrite.
* `PUT /tmp/file.txt` Upload indicated file to the FTP
* `PASV` This will open a passive connection and will indicate the user were he can connects
* `TYPE i` Set transfer to binary
* `REST 6` This will indicate the server that next time it send something using `RETR` it should start in the 6th byte.
* `RETR /path/to/file` A passive or a port connection must be establish. Then, the FTP server will send the indicated file through that connection

## vsFTPd

One of the most used FTP Servers on Linux-based OS is **vsFTPd**.

### Default Configuration location

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

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption><p>Nmap report</p></figcaption></figure>

### vsFTPd exploits

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>
