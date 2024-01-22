# How-To: 

## Basic UNIX stuff
### networky commands
- `ssh`
- `openssl`
- `nmap`
- `ping`
- `nc`
    - -l (set up listener for tcp connections)
    - -vnp
- `netstat`

### permissions
- `chmod`
    - chmod 644 = 110 100 100 = rw- r- -   r- - 
- `chown`
- `setuid` (run process as another user)
### "normal" commands
- `cd`
- `ls`
    - -l (see more info)
    - -a (see all files, ones that start w/ a dot)
    - -h
- `grep`
- `cat`
- `find`
- `file`
- `vi`
    - `vim`
    - `:q`
    - `:wq`
- `echo`
    - `echo hello | wc -c`
    - `wc -c <<< hello` same as line above

- `tr`
- `exit`
- `diff`
    - `diff decrypted.txt plain.txt`
- `man`
### Operators?
- `<`
- `>`
- `|`
- `2>/dev/null`

## GDB
- layout:
    - `lay asm`
    - `lay src`
- step through
    - `continue` or `c`
    - `next` or `n`
    - `step` or `c`
- print some things
    - `x/20xw $rsp`
    - get memory address of main
        - `p main`
    - `x/ni ADDR`
- breaks
    - `br main`
    - `br 1`
    - `br *0x...`


## IP etc
### Get the computer's IP address for the current internet connection:
- `ipconfig`
    - Lots of info
- `ipconfig getifaddr en0`
    - Just the ip address
- `ifconfig`
- In theory…
    - `hostname –i` (on kali)
    - `hostname -f` (on mac)
    - `ip a`

### Determine an ip address with a hostname
- ping \<hostname\>
- dig \<hostname\>
- traceroute \<hostname\>
    - ex `traceroute bad.horse`
- host \<hostname\>

### Determine the hostname with a given ip address
- nslookup \<ip\>
- DNSlytics (a website)

### See routing table:
- `netstat -r`
    - `netstat -rn` (take mask, mask address, with the gen mask, if ==dest, use gateway to send.)
- arp -a ?

## Port things
### How to tell if a process is listening on a given port on a given host?
- `netstat -tuln | grep 80`
    - Check if process listening on a port
- `netstat -tuln | grep 80 | grep 137.22.94.116`
    - Check if a process is listening on a port on a host
-  `lsof`
    - List open files

### How can you tell which ports have processes listening on them on a given host?
- netstat -tuln <host>
- nmap 
    - nmap <ip> checks the 1000 most common ports
    - nmap -p- <ip> checks ports 1-65535. (slow)

## Files
### Copy a file using CLA
- SFTP (secure file transfer protocol)
    - sftp helmboldk@mantis.mathcs.carleton.edu
    - put CS208/prefecting/test.c
- SCP
    - 1 line

### Retrieve and Save a given webpage
- `curl -o <output.html>l https://carleton.edu`
- `wget https://carleton.edu`
    - Saves in a file name it gets from the server

## HTTP
### How can you view the HTTP headers that your computer sends to the web server when you do the tasks in the previous two questions?
- `curl -v carleton.edu`

### How can you view the HTTP headers sent back from a specified web server when you request one of its pages?
- `curl -I carleton.edu`


## Burpsuite and Wireshark
### Select just an ip and port
- ip.addr == \<ip\> and tcp.port == 80

### install burpsuite
- `sudo apt update`
- `sudo apt install burpsuite`

## Hashing & Keys and things
- Generate random 16-byte (32-hexadecimal-digit) key
    - `openssl rand 16 | od -An -tx1 | tr -d ' \n'`
    - `openssl rand -hex 16``
    - Ex. `IV=$(openssl rand -hex 16)`
        - One random block
        - `echo $IV`
- Key = `openssl rand -hex 16`
    - `echo $Key``
- Hashing 
    - `shasum -a 256 moose.txt`


