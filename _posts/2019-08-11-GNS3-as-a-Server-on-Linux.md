---
layout: post
author: Omar N
---

GNS3 is an astonishing tool to emulate Cisco network topologies. But if it is done as a basic installation on a Windows computer; GNS3 can start consuming high amounts of resources when the transition from simple to more complex network topologies happens, and it wouldn’t be possible to setup advanced switching operations.

One solutions, to avoid the issues mentioned. It is to install GNS3 on Linux as a server and then connect a GNS3 client from any other computer running Windows or Mac.

Therefore, this document will show **how to setup GNS3 as a server on Ubuntu and GNS3 as a client on Windows in more detail than the official documentation.**

[![Watch the video](https://img.youtube.com/vi/4yelKWsP3OQ/hqdefault.jpg)](https://youtu.be/4yelKWsP3OQ)

## Pre requisites

It is fundamental to have basic experience on:

- Using Packet Tracer and GNS3 on Windows or Linux with basic Routing and Switching configuration.

- Installing Linux OSes.

- Being a CCNA candidate.

- Configuring a couple of cisco routers and switches.

## Installing Ubuntu Server 16.04 LTS

Even though Ubuntu released its 18.04 LTS version, the official GNS3 documentation suggest installing a fresh Ubuntu 16.04 LTS server. Thus, it is recommended to follow the next steps.

Go to [Ubuntu](https://releases.ubuntu.com/xenial/) and download the appropriate image according to your CPU architecture. For example for a Core i5 (AMD64)

![Ubuntu1604](/assets/images/2019-08-11-GNS3-as-a-Server-on-Linux/downloadUbuntu_16.04_1024x343.jpg "Download Ubuntu 16.04")

*Example for Intel Corei5 AMD64*

It is a good option to create a bootable USB Ubuntu Server with [Rufus](https://rufus.ie/en/)

![RufusHashing](/assets/images/2019-08-11-GNS3-as-a-Server-on-Linux/Rufus_Hashing_600x908.jpg "Rufus Hashing")

*Get the hash values from Rufus*

![Rufus Default](/assets/images/2019-08-11-GNS3-as-a-Server-on-Linux/Rufus_DefaultOptions_477x785.jpg "Rufus Defaul")

*Rufus default options*

![Rufus DD Image](/assets/images/2019-08-11-GNS3-as-a-Server-on-Linux/Rufus_DD_Image_Mode_612x785.jpg "Rufus DD Image")

*DD image mode*

Start Ubuntu Installation. Follow the official documentation tutorial for [Installing Ubuntu Server 16.04.](https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-server-1604#0) The main tips for a correct installation are:

- Make sure to have Internet connectivity

- Be very careful with disk partitioning

- Choose NO AUTOMATIC UPDATES

- Select standard system utilities and OpenSSH Server software

After the installation has finished. Update and Upgrade the new fresh Ubuntu Server

```Shell
sudo apt-get update
sudo apt-get upgrade
sudo reboot
```

## GNS3 Server Installation

Installing as a root

```
cd /tmp/
sudo curl https://raw.githubusercontent.com/GNS3/gns3-server/master/scripts/remote-install.sh > gns3-remote-install.sh
sudo bash gns3-remote-install.sh --with-openvpn --with-iou --with-i386-repository
sudo reboot
```

Check GNS3 server version

```
gns3server -v
```
Finally, download the VPN certificate from */root/client.opvn*

## Install and configure OpenVPN on Windows

Go to [openvpn.net](https://openvpn.net/community-downloads/) and download the appropriate file

Make sure the OpenVPN configuration file client.ovpn has the right server IP address

![OpenVPN config file](/assets/images/2019-08-11-GNS3-as-a-Server-on-Linux/openVPN_configFile_400x267.jpg "OpenVPN config file")

*OpenVPN configuration file*

Import configuration file

![OpenVPN Import 1](/assets/images/2019-08-11-GNS3-as-a-Server-on-Linux/openVPN_import01_183x170.jpg "OpenVPN Import")

*Go to Hidden Icons and right click on OpenVPN*

![OpenVPN Import 2](/assets/images/2019-08-11-GNS3-as-a-Server-on-Linux/openVPN_import02_234x171.jpg "OpenVPN Import")

*Select Import file*


![OpenVPN Import 3](/assets/images/2019-08-11-GNS3-as-a-Server-on-Linux/openVPN_import03_619x363.jpg "OpenVPN Import")

*Look up the configuration file*

> Notice: To be consistent the name of client.ovpn file was changed to gns3Server.ovpn, before to import

Make a VPN connection


![OpenVPN Connect](/assets/images/2019-08-11-GNS3-as-a-Server-on-Linux/openVPN_connect_325x365.jpg "OpenVPN Connect")

*Make a VPN connection*

The link [http://172.16.253.1:3080/](http://172.16.253.1:3080/) should work

![OpenVPN Link](/assets/images/2019-08-11-GNS3-as-a-Server-on-Linux/openVPN_link_631x373.jpg "OpenVPN Link")

*Making sure the VPN connection is working*

## Set Up GNS3 Client on Windows

- Go to gns3 and download the version for windows

- Install GNS3 with default options

- Start and configure GNS3 as a client

![GNS client configuration](/assets/images/2019-08-11-GNS3-as-a-Server-on-Linux/GNS3client01_801x692.jpg "GNS client configuration")

*GNS client configuration*

![GNS Server IP](/assets/images/2019-08-11-GNS3-as-a-Server-on-Linux/GNS3client02_802x688.jpg "GNS Server IP")

*Host is the IP address of the GNS3 server*

![GNS client summary](/assets/images/2019-08-11-GNS3-as-a-Server-on-Linux/GNS3client03_805x691.jpg "GNS client summary")

*GNS3 client summary configuration*

![No appliances](/assets/images/2019-08-11-GNS3-as-a-Server-on-Linux/GNS3client04.jpg "No appliances")

*Add later appliances*

![No projects](/assets/images/2019-08-11-GNS3-as-a-Server-on-Linux/GNS3client05.jpg "No projects")

*Add later a project*

![GNS3 connection](/assets/images/2019-08-11-GNS3-as-a-Server-on-Linux/GNS3client06_300x229.jpg "GNS3 connection")

*Main server should be with green light*

## Conclusions

The advantages having GNS3 as a server on Linux are:

- It is possible to configure almost any advanced Routing and Switching lab. Therefore, it is better than having a full hardware stack of routers and switches.

- It speeds up the process of jumping from one topology to another. The same process with real cisco devices can take a much longer time

- It has much more IOS commands than Packet Tracer

- It is truly stable

- It doesn’t consume a large quantities of computer resources as it does on a single Windows installation

- It is possible to lab advanced switching

- Very useful for CCNA and CCNP candidates

## Appendix and Updates

If it is needed to change network configuration on Linux

```
sudo vim /etc/network/interfaces

```

![Ubuntu DHCP](/assets/images/2019-08-11-GNS3-as-a-Server-on-Linux/UbuntuNetworkDHCP.jpg "Ubuntu DHCP")

*Ubuntu DHCP*

![Ubuntu IP static](/assets/images/2019-08-11-GNS3-as-a-Server-on-Linux/UbuntuNetworkStatic.jpg "Ubuntu IP static")

*Ubuntu IP static*
