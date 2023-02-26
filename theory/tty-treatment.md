# How to make a TTY Treatment
When we get access to a server via Reverse Shell, we need to make a TTY Treatment in order to have a full interactive shell.
## First Way

```bash
$ script /dev/ null -c bash
www-data@server$ 
[CTRL + Z]
root@localhost$ stty raw -echo;fg
			reset xterm
www-data@server$  export TERM=xterm
www-data@server$  export SHELL=bash
www-data@server$ stty rows 44 columns 184
```

## Second way

We only need to add a ``rlwrap`` in the beginning of the ``nc -nvlp <PORT>`` to have a full interactive shell.
