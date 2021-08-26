---
title: "How to install Ubuntu Server on a Raspberry Pi 4 model B in 3 steps (The easiest way) "
date: 2021-08-23T15:34:20+02:00
draft: false
tags: [raspberry, linux, ubuntu server, fedora]
---

**Things you need:**
- A Raspberry Pi 4 model B 
- An Ethernet Cable
- A proper power supply for your Raspberry Pi 
- An SD Card compatible with your Raspberry

I’m assuming that you already have a computer with an SD card slot and an internet connection. 

I will be using a laptop with Fedora 34 workstation as an “external computer”. But you can follow these steps if you are on other distributions, MacOS or Windows.

## Write the SO image in your SD card

Firstly plug in your SD card into your computer.

Then, download the Raspberry Pi Imager software from https://www.raspberrypi.org/software/.

If you are using a different Linux distro than Ubuntu, you can install it through snap.

Once you have it installed, open Raspberry Pi Imager.

Choose os:
- Select “Other general purpose OS”
- Select “Ubuntu”
- Select “Ubuntu Server 20.04.2 LTS (RPi 3/4/400)”

Choose storage:
- Select your SD card

Click write and wait until the process is finished. If you have no errors you can go on! Otherwise I recommend you to follow STFW and RDFM standards :P

## Check if your hardware actually works

You don’t want to wait to check if your raspberry actually works once you have set up the fan and screwed the case on, right?

So plug in the SD card and then the power supply, if you can see a red light (power supply) and a green light (SO sd card) then you are on a roll! Keep going! 
## Connect (locally) to your Raspberry Pi through SSH

Before you access it, you will need **to know the IP of your Raspberry Pi**. The easiest way to find out what its IP is, is to **login into your router and look at all the devices connected to your network**. 

In my case, the device was named “ubuntu” and its IP was 192.168.0.19

If you are on Linux/MacOS, I assume that you have already installed open-ssh. If you are on Windows I assume that you have already installed putty or cygwin 

So, open your terminal and type:
{{< cmd >}}
ssh username@hostname
{{< /cmd >}}

The username is "ubuntu" by default. The hostname is your Raspberry Pi IP, as I said just above, mine is "192.168.0.19". So the whole command shoud look like this:

{{< cmd >}}
ssh ubuntu@192.168.0.19
{{< /cmd >}}


Press Enter. You will have to add this new host to your known hosts list typing `yes`. When the terminal asks you for a password type the default password `ubuntu`. Also, you will have to change the password. Use a strong one! 

At this point you are already connected to your Ubuntu Server.

## Final thoughts and other resources
**There are endless approaches to achieve exactly the same thing**. I only described one way. So feel free to pick whichever most suits your needs, skills or knowledge. :)

If you find any errors/mistakes in this text, please [email me](mailto:joji@dearalgorithm.com)!

If you need help with the process described above and you already tried SFDW and RDFM, then please [email me](mailto:joji@dearalgorithm.com)!

### resources
[Get Fedora Workstation](https://getfedora.org/)  
[Download Raspberry Pi Imager](https://www.raspberrypi.org/software/)  
[A more detailed guide from Ubuntu website](https://ubuntu.com/tutorials/how-to-install-ubuntu-on-your-raspberry-pi)  
[Open SSH manual](https://www.openssh.com/manual.html)  
[6 Causes for a Raspberry Pi That Won't Boot \(And How to Fix Them\)](https://www.makeuseof.com/tag/raspberry-pi-wont-boot-fix/)