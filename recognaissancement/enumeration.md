# Enumeration

## Enumeration

The **Enumeration** phase, on the other hand, refers to the process of gatherting detailed information about the services and applications identified in the reconnaissance phase. This may include analyzing open services, identifying users and users groups, file and directory permissions, and searching potential vulnerabilities in the services and applications. **Enumeration** is an important phase for identifying potential attack vectors and planning for the following phases of the pentesting.

Here are some tips for enumeration:

1. Use a variety of tools: There are many tools available for enumeration, such as Nmap, Nessus, and Metasploit. It's important to use a variety of tools to gather as much information as possible about the target system.
2. Enumerate open ports and services: Identify all open ports and services on the target system using tools such as Nmap. Once you have identified the open ports and services, you can use tools such as Nessus to identify vulnerabilities in those services.
3. Enumerate users and groups: Identify all users and groups on the target system using tools such as enum4linux, rpcclient, or Metasploit. Once you have identified the users and groups, you can use tools such as John the Ripper or Hashcat to crack their passwords.
4. Enumerate files and directories: Identify all files and directories on the target system using tools such as dirb, Dirbuster, or Metasploit. Once you have identified the files and directories, you can use tools such as Hydra to brute-force any password-protected files.
5. Enumerate the network: Identify all other devices and systems on the network using tools such as Nmap. This can help you identify potential attack vectors and plan your attack accordingly.
6. Enumerate application-specific information: If the target system is running specific applications, such as a web application or database, it's important to use tools that are designed for that application to gather information. For example, you can use Burp Suite to identify vulnerabilities in web applications or sqlmap to identify vulnerabilities in databases.

Remember that enumeration is just one phase of pentesting, and it's important to use a comprehensive approach that includes other phases, such as vulnerability scanning and exploitation. Also, ensure that you have the appropriate permissions and authorization before performing any enumeration or other activities on the target system.



# Web Enumeration

We can use tools like gobuster, wfuzz, ffuf, etc. To enumerate directories in a web.

## gobuster - directory search

We can use gobuster to search directories adn files in a web
```bash
gobuster dir -u http://<TARGET> -w <WORDLIST> -t <THREADS> -x php,html,txt,asp,js
```

## gobuster - vhost search

We can use gobuster to search for Virtual Hosts
```bash
gobuster vhost -u http://<TARGET> -w <WORDLIST> -t <THREADS>
```

## gobuster - dns search

We can use gobuster to search for subdomains like **dev.example.com** 
```bash
gobuster dns -w <WORDLIST> -d <URL.COM> -t <THREADS>
```

## wfuzz - directory search

We can use wfuzz to search directories in a web
```bash
wfuzz -c -w <WORDLIST> -u <TARGET>/FUZZ -t <THREADS> --hc <CODE TO HIDE>
```

## wfuzz - archive search

We can use wfuzz to search files in a web
```bash
wfuzz -c -w <WORDLIST> -u <TARGET>/FUZZ.<EXTENSION> -t <THREADS> --hc <CODE TO HIDE>
```

## wfuzz - fuzzing parameters in URL

We can use wfuzz to search into parameters in a URL
```bash
wfuzz -c -z range,0-10 -u <TARGET>/listproducts.php?cat=FUZZ -t <THREADS>
```

## wfuzz - fuzzing with a proxy

We can use wfuzz to search directories or whatever with a proxy
```bash
wfuzz -c -w <WORDLIST> -u <TARGET>/FUZZ.<EXTENSION> -t <THREADS> --hc <CODE TO HIDE> -p localhost:8080
```

## wfuzz - fuzzing with a proxy using SOCKS4/5
```bash

wfuzz -c -w <WORDLIST> -u <TARGET>/FUZZ.<EXTENSION> -t <THREADS> --hc <CODE TO HIDE> -p localhost:8080:SOCKS5/4
```

## wfuzz  - authentication

We can use wfuzz to search for a valid authentication
```bash
wfuzz -z list,nonvalid-httpwatch --basic FUZZ:FUZZ <URL>
```