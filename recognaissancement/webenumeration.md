# Web Enumeration

We can use tools like gobuster, wfuzz, ffuf, etc. To enumerate directories in a web.

# Gobuster

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

# Wfuzz
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
