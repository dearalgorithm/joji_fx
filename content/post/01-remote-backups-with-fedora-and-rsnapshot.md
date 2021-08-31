---
title: "How to backup files remotely from Fedora Server 34 to Fedora Workstation 34"
date: 2021-08-27T20:30:03+02:00
draft: false
tags: [linux, fedora, fedora server, backup, rsnapshot, ssh]
---

**Things you will need:**
- An internet connection or a local area network
- A computer/virtual machine with Fedora Workstation installed
- A computer/virtual machine with Fedora Server Installed

Let’s assume that you have a Fedora Workstation 34 machine with the purpose of saving backups on it. 

Also, you have a Fedora Server 34. You know the root’s password and you checked `Allow root SSH login with password` during the installation. 

If you need to add your username to sudoers, reboot the machine, log in as root and type `usermod -aG wheel yourusername` 

If you need to edit SSH root access you can type `sudo vim /etc/ssh/sshd_config` and uncomment or write these lines:

```conf
PasswordAuthentication yes
PermitRootLogin yes
```

## Creating a SSH pair keys on your Workstation and adding the public key to your Server

**This commands should be run on your Fedora Workstation**

{{< cmd >}}
ssh-keygen -f yourkeyfilename
{{< /cmd >}}

You can leave the passphrase empty.

Then you can copy the public key to your Fedora Server typing this:

{{< cmd >}}
ssh-copy-id -i ~/.ssh/yourkeyfilename.pub root@server
{{< /cmd >}}

-i identifies file, also you can know your `server` IP by typing hostname -I on your Fedora Server

After adding your key, you can try connecting to your server by ssh:
{{< cmd >}}
ssh root@server
{{< /cmd >}}

You can know your `server` IP by typing hostname -I on your Fedora Server


## Configuring and automatizing your backups with rsnapshot and cron jobs

**This commands should be run on your Fedora Workstation**

First of all, install rsnapshot:
{{< cmd >}}
sudo dnf install rsnapshot
{{< /cmd >}}

Then edit rsnapshot conf file, but first backup it! (just in case).
{{< cmd >}}
sudo cp /etc/rsnapshot.conf /etc/rsnapshot.conf.backup
{{< /cmd >}}

Now you can edit it safely:
{{< cmd >}}
sudo cp /etc/rsnapshot.conf
{{< /cmd >}}

Actually before you edit, I suggest that you read the rsnapshot man page, it’s quite short and you will be able to know how rsnapshot works, including its config file, so go for it!

https://linux.die.net/man/1/rsnapshot

Or you can just copy-paste this configuration:

```conf
config_version    1.2

snapshot_root    /home/user/backups/

cmd_cp        /usr/bin/cp
cmd_rm        /usr/bin/rm
cmd_rsync    /usr/bin/rsync
cmd_ssh    /usr/bin/ssh
cmd_logger    /usr/bin/logger
cmd_du        /usr/bin/du

retain    hourly    6
retain    daily    7
retain    weekly    4
retain    monthly    3

backup    root@server:/home/    fedoraserver/
```

Remember to provide your desired path on the “snapshot_root” option. And also remember to provide your server path on the “backup” option. 

Now it’s time to test your config file:

{{< cmd >}}
rsnapshot configtest
{{< /cmd >}}

If you get a “Syntax OK” then you can generate your first backup:
{{< cmd >}}
rsnapshot hourly
{{< /cmd >}}

According your config file, your backup should be placed on `/home/user/backups/fedoraserver/`

**If you don’t want to automate or schedule your backups, then you are done** and free to go! :)

Otherwise, keep reading!

### How to set up a cron job for rsnapshot

Create a cron file:
{{< cmd >}}
$ sudo vim /etc/cron.d/rsnapshot
{{< /cmd >}}

```
0       */4      * * *   root   /usr/bin/rsnapshot hourly
30      3       * * *   root    /usr/bin/rsnapshot daily
0       3       * * 1   root    /usr/bin/rsnapshot weekly
30      2       1 * *   root    /usr/bin/rsnapshot monthly
```

Save it and, voilà! You’re done :)

*Now you have your backup system up and running. Congratulations!*


## Final thoughts and other resources
**There are endless approaches to achieve exactly the same thing**. I only described one way. So feel free to pick whichever most suits your needs, skills or knowledge. :)

If you find any errors/mistakes in this text, please [email me](mailto:joji@dearalgorithm.com)!

If you need help with the process described above and you already tried SFDW and RDFM, then please [email me](mailto:joji@dearalgorithm.com)!

### resources
[Get Fedora](https://getfedora.org/)  
[Open SSH manual](https://www.openssh.com/manual.html)  
[rsnapshot manual](https://linux.die.net/man/1/rsnapshot)
