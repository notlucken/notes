# Reconnaissance

The **Reconnaissance** phase refers to the process of gathering Informatin about the Target System, including identifying devices and services on the network, and identifying potential vulnerabilities in the operating systems and applications used on the target.

### Identifying a Target

To identify a target, you can use a few tools of Linux:

#### arp-scan

You can use the tool called **arp-scan** to enumerate all devices on your network.

```bash
sudo arp-scan --localnet
```

This will scan your local network and show the MAC and IP addresses of connected devices.

#### fping

fping is a tool that can be used to ping multiple hosts in parallel, making it faster than the regular ping command.

```bash
sudo fping -a -g 192.168.100.0/24
```

This will scan all IP addresses in the range of 192.168.1.0 to 192.168.1.255 and show the devices that are online.

Now that we identified the target, we can proceed to Reconnaissance phase.

### Nmap

Nmap is a powerful tool for network exploration and security auditing that can be used for reconnaissance in a pentesting engagement.

First of all, we need to install Nmap.

If you're in Linux:

```bash
sudo apt install nmap
```

If you're in Windows:

[Nmap in Windows](https://nmap.org/download.html)

#### What I recommend to do to Scan

What I do everytime that I do an Scan to a device, it's this:

```bash
sudo nmap -p- --open --min-rate 5000 -Pn -n -vvv -sS <IP> -oG allPorts
```

Explanatinon:

| Argument        | Description                                                     |
| --------------- | --------------------------------------------------------------- |
| -p-             | Scan all ports (66535)                                          |
| --open          | Report only open ports                                          |
| --min rate 5000 | Send packets no slower than 5000 per second                     |
| -Pn             | Skip host discovery                                             |
| -n              | Do not do DNS resolution                                        |
| -vvv            | Triple verbose                                                  |
| -sS             | TCP SYN Scan                                                    |
| -oG allPorts    | Export the scan in a grepeable format in a file called allPorts |

Why I do this:

[S4vitar](https://twitch.tv/S4vitaar), he's a Cyber Security streamer, and he do this in order to win time in the scans, because them can be so slow.

After the command, the output will be some like this:&#x20;

We can use a tool called **extractPorts** (S4vitar) to extract the open ports and copy them in out clipboard:

```bash
  # Extract nmap information  
  function extractPorts(){
      ports="$(cat $1 | grep -oP '\d{1,5}/open' | awk '{print $1}' FS='/' | xargs | tr ' ' ',')"
      ip_address="$(cat $1 | grep -oP '\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}' | sort -u | head -n 1)"
    echo -e "\n[*] Extracting information...\n" > extractPorts.tmp
    echo -e "\t[*] IP Address: $ip_address"  >> extractPorts.tmp
    echo -e "\t[*] Open ports: $ports\n"  >> extractPorts.tmp
    echo $ports | tr -d '\n' | xclip -sel clip
    echo -e "[*] Ports copied to clipboard\n"  >> extractPorts.tmp
    cat extractPorts.tmp; rm extractPorts.tmp
}
```

You can put this function in your **.zshrc** or in your **.bashrc**

Figure it that you need to have installed **xclip**. If you don't have it, run the command:

```bash
sudo apt install xclip
```

So the output of extracPorts will be this:

Now the ports will be copied into our clipboard, and we can proceed with the next command:

```bash
nmap -p<PORTS> -sCV <IP> -oN targeted
```

Explanation:

| Flag         | Description                                                             |
| ------------ | ----------------------------------------------------------------------- |
| -p PORTS     | Here you need to paste the extracted ports in the previous command      |
| -sCV         | This is a fusion between two flags, **-sC** and **-sV**                 |
| -oN targeted | Export the information in a legible format into the file named targeted |

The output file of the previous command will be something like this:&#x20;

So we can use this to proceed with the **Enumeration** phase.
