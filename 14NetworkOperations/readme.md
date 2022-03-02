# Chapter 14: Network Operations #

## Introduction ##

### Learning Objectives ###

By the end of this chapter, you should be able to:

* Explain basic networking concepts, including types of networks and addressing issues.
* Configure network interfaces and use basic networking utilities, such as ifconfig, ip, ping, route and traceroute.
* Use graphical and non-graphical browsers, such as Lynx, w3m, Firefox, Chrome and Epiphany.
* Transfer files to and from clients and servers using both graphical and text mode applications, such as Filezilla, ftp, sftp, curl and wget.

## Network Addresses and DNS ##

### Introduction to Networking ###

A network is a group of computers and computing devices connected together through communication channels, such as cables or wireless media. The computers connected over a network may be located in the same geographical area or spread across the world.

A network is used to:

* Allow the connected devices to communicate with each other
* Enable multiple users to share devices over the network, such as music and video servers, printers and scanners.
* Share and manage information across computers easily.

Most organizations have both an internal network and an Internet connection for users to communicate with machines and people outside the organization. The Internet is the largest network in the world and can be called "the network of networks".

### IP Addresses ###

Devices attached to a network must have at least one unique network address identifier known as the IP (Internet Protocol) address. The address is essential for routing packets of information through the network.

Exchanging information across the network requires using streams of small packets, each of which contains a piece of the information going from one machine to another. These packets contain data buffers, together with headers which contain information about where the packet is going to and coming from, and where it fits in the sequence of packets that constitute the stream. Networking protocols and software are rather complicated due to the diversity of machines and operating systems they must deal with, as well as the fact that even very old standards must be supported.

![ip image](https://courses.edx.org/assets/courseware/v1/6aefe557b5aedfc43e2983372dd202d0/asset-v1:LinuxFoundationX+LFS101x+2T2021+type@asset+block/LFS01_ch11_screen04.jpg)

### IPv4 and IPv6 ###

There are two different types of IP addresses available: IPv4 (version 4) and IPv6 (version 6). IPv4 is older and by far the more widely used, while IPv6 is newer and is designed to get past limitations inherent in the older standard and furnish many more possible addresses.

IPv4 uses 32-bits for addresses; there are only 4.3 billion unique addresses available. Furthermore, many addresses are allotted and reserved, but not actually used. IPv4 is considered inadequate for meeting future needs because the number of devices available on the global network has increased enormously in recent years.

IPv6 uses 128-bits for addresses; this allows for 3.4 X 1038 unique addresses. If you have a larger network of computers and want to add more, you may want to move to IPv6, because it provides more unique addresses. However, it can be complex to migrate to IPv6; the two protocols do not always inter-operate well. Thus, moving equipment and addresses to IPv6 requires significant effort and has not been quite as fast as was originally intended. We will discuss IPv4 more than IPv6 as you are more likely to deal with it.

One reason IPv4 has not disappeared is there are ways to effectively make many more addresses available by methods such as NAT (Network Address Translation).  NAT enables sharing one IP address among many locally connected computers, each of which has a unique address only seen on the local network. While this is used in organizational settings, it also used in simple home networks. For example, if you have a router hooked up to your Internet Provider (such as a cable system) it gives you one externally visible address, but issues each device in your home an individual local address.

![ip image](https://courses.edx.org/assets/courseware/v1/fa98328f7ff2e180a79cead9ee3e433f/asset-v1:LinuxFoundationX+LFS101x+2T2021+type@asset+block/LFS01_ch11_screen05.jpg)

### Decoding IPv4 Addresses ### 

A 32-bit IPv4 address is divided into four 8-bit sections called octets.

Example:
IP address →        172  .    16  .   31   .  46
Bit format →     10101100.00010000.00011111.00101110

NOTE: Octet is just another word for byte.

Network addresses are divided into five classes: A, B, C, D and E. 
Classes A, B and C are classified into two parts: 
* Network addresses (Net ID) and 
* Host address (Host ID). 

The Net ID is used to identify the network, while the Host ID is used to identify a host in the network. 

Class D is used for special multicast applications (information is broadcast to multiple computers simultaneously) and Class E is reserved for future use. In this section you will learn about classes A, B and C.

![image classes](https://courses.edx.org/assets/courseware/v1/610943ad6bb219df591ec8659288e630/asset-v1:LinuxFoundationX+LFS101x+2T2021+type@asset+block/LFS01_ch11_screen06.jpg)

### Class A Network Addresses ###

Class A addresses use the first octet of an IP address as their Net ID and use the other three octets as the Host ID. The first bit of the first octet is always set to zero. So you can use only 7-bits for unique network numbers. As a result, there are a maximum of 126 Class A networks available (the addresses 0000000 and 1111111 are reserved). Not surprisingly, this was only feasible when there were very few unique networks with large numbers of hosts. As the use of the Internet expanded, Classes B and C were added in order to accommodate the growing demand for independent networks.

Each Class A network can have up to 16.7 million unique hosts on its network. The range of host address is from 1.0.0.0 to 127.255.255.255.

NOTE: The value of an octet, or 8-bits, can range from 0 to 255. 

![class A](https://courses.edx.org/assets/courseware/v1/1867a1e02d2827251e50b65a03bcaa1b/asset-v1:LinuxFoundationX+LFS101x+2T2021+type@asset+block/LFS01_ch11_screen07.jpg)

### Class B Network Addresses ###

Class B addresses use the first two octets of the IP address as their Net ID and the last two octets as the Host ID. The first two bits of the first octet are always set to binary 10, so there are a maximum of 16,384 (14-bits) Class B networks. The first octet of a Class B address has values from 128 to 191. The introduction of Class B networks expanded the number of networks but it soon became clear that a further level would be needed.

Each Class B network can support a maximum of 65,536 unique hosts on its network. The range of host addresses is from 128.0.0.0 to 191.255.255.255.

![class B](https://courses.edx.org/assets/courseware/v1/7e40d0c228a2ac28dd4e1e9af18ba3ce/asset-v1:LinuxFoundationX+LFS101x+2T2021+type@asset+block/LFS01_ch11_screen08.jpg)

### Class C Network Addresses ###

Class C addresses use the first three octets of the IP address as their Net ID and the last octet as their Host ID. The first three bits of the first octet are set to binary 110, so almost 2.1 million (21-bits) Class C networks are available. The first octet of a Class C address has values from 192 to 223. These are most common for smaller networks which don't have many unique hosts.

Each Class C network can support up to 256 (8-bits) unique hosts. The range of host addresses is from 192.0.0.0 to 223.255.255.255.

![class C eg](https://courses.edx.org/assets/courseware/v1/376a6fe8144e0d5799f331a803e1d33d/asset-v1:LinuxFoundationX+LFS101x+2T2021+type@asset+block/LFS01_ch11_screen09.jpg)

### IP Address Allocation ###

Typically, a range of IP addresses are requested from your Internet Service Provider (ISP) by your organization's network administrator. Often, your choice of which class of IP address you are given depends on the size of your network and expected growth needs. If NAT is in operation, such as in a home network, you only get one externally visible address!

![ip allocation](https://courses.edx.org/assets/courseware/v1/303c5dc5b32edde05f599cac40512b7d/asset-v1:LinuxFoundationX+LFS101x+2T2021+type@asset+block/LFS01_ch11_screen10a.jpg)

You can assign IP addresses to computers over a network either manually or dynamically. Manual assignment adds static (never changing) addresses to the network. Dynamically assigned addresses can change every time you reboot or even more often; the Dynamic Host Configuration Protocol (DHCP) is used to assign IP addresses.

### Name Resolution ###

Name Resolution is used to convert numerical IP address values into a human-readable format known as the hostname. For example, 104.95.85.15 is the numerical IP address that refers to the hostname whitehouse.gov. Hostnames are much easier to remember!

Given an IP address, you can obtain its corresponding hostname. Accessing the machine over the network becomes easier when you can type the hostname instead of the IP address.

You can view your system’s hostname simply by typing hostname with no argument.

NOTE: If you give an argument, the system will try to change its hostname to match it, however, only root users can do that.

The special hostname localhost is associated with the IP address 127.0.0.1 and describes the machine you are currently on (which normally has additional network-related IP addresses).

![eg hostname](https://courses.edx.org/assets/courseware/v1/c4e92d4d86a678c688c053c06672df41/asset-v1:LinuxFoundationX+LFS101x+2T2021+type@asset+block/LFS01_ch11_screen12.jpg)

## Networking Configuration and Tools ##

### Network Configuration Files ###

Network configuration files are essential to ensure that interfaces function correctly. They are located in the /etc directory tree. However, the exact files used have historically been dependent on the particular Linux distribution and version being used.

For Debian family configurations, the basic network configuration files could be found under /etc/network/, while for Red Hat and SUSE family systems one needed to inspect /etc/sysconfig/network.

Modern systems emphasize the use of Network Manager, which we briefly discussed when we considered graphical system administration, rather than try to keep up with the vagaries of the files in /etc. While the graphical versions of Network Manager do look somewhat different in different distributions, the nmtui utility (shown in the screenshot) varies almost not at all, as does the even more sparse nmcli (command line interface) utility. If you are proficient in the use of the GUIs, by all means, use them. If you are working on a variety of systems, the lower level utilities may make life easier.


![network manager](https://courses.edx.org/assets/courseware/v1/30ad387df9ee4d04b71b8a402855df8c/asset-v1:LinuxFoundationX+LFS101x+2T2021+type@asset+block/nmtui.png)

Recent Ubuntu distributions include netplan, which is turned on by default, and supplants Network Manager. Since no other distribution has shown interest, and since it can easily be disabled if it bothers you, we will ignore it.

### Network Interfaces ###

Network interfaces are a connection channel between a device and a network. Physically, network interfaces can proceed through a network interface card (NIC), or can be more abstractly implemented as software. You can have multiple network interfaces operating at once. Specific interfaces can be brought up (activated) or brought down (de-activated) at any time.

Information about a particular network interface or all network interfaces can be reported by the ip and ifconfig utilities, which you may have to run as the superuser, or at least, give the full path, i.e. /sbin/ifconfig, on some distributions. ip is newer than ifconfig and has far more capabilities, but its output is uglier to the human eye. Some new Linux distributions do not install the older net-tools package to which ifconfig belongs, and  so you would have to install it if you want to use it.


### The ip Utility ###

To view the IP address:

    $ /sbin/ip addr show

To view the routing information:

    $ /sbin/ip route show

ip is a very powerful program that can do many things. Older (and more specific) utilities such as ifconfig and route are often used to accomplish similar tasks. A look at the relevant man pages can tell you much more about these utilities.

![this is ip image](https://courses.edx.org/assets/courseware/v1/a863fadf4376afe31b1e3fea08fcc1cc/asset-v1:LinuxFoundationX+LFS101x+2T2021+type@asset+block/iprhel7.png)

### ping ###

ping is used to check whether or not a machine attached to the network can receive and send data; i.e. it confirms that the remote host is online and is responding.

To check the status of the remote host, at the command prompt, type ping <hostname>.

ping is frequently used for network testing and management; however, its usage can increase network load unacceptably. Hence, you can abort the execution of ping by typing CTRL-C, or by using the -c option, which limits the number of packets that ping will send before it quits. When execution stops, a summary is displayed.

### route ###

A network requires the connection of many nodes. Data moves from source to destination by passing through a series of routers and potentially across multiple networks. Servers maintain routing tables containing the addresses of each node in the network. The IP routing protocols enable routers to build up a forwarding table that correlates final destinations with the next hop addresses.

![ip route eg](https://courses.edx.org/assets/courseware/v1/fe2820385b830a22cf8deccad8e0428c/asset-v1:LinuxFoundationX+LFS101x+2T2021+type@asset+block/routeubuntu.png)

One can use the route utility or the newer ip route command to view or change the IP routing table to add, delete, or modify specific (static) routes to specific hosts or networks. The table explains some commands that can be used to manage IP routing:

Task 	                      |  Command
----------------------------- | ------------------------------------------
Show current routing table 	  |  $ route –n or ip route
Add static route 	          |  $ route add -net address or ip route add
Delete static route 	      |  $ route del -net address or ip route del

### traceroute ###

traceroute is used to inspect the route which the data packet takes to reach the destination host, which makes it quite useful for troubleshooting network delays and errors. By using traceroute, you can isolate connectivity issues between hops, which helps resolve them faster.

To print the route taken by the packet to reach the network host, at the command prompt, type traceroute <address>.

![trace route](https://courses.edx.org/assets/courseware/v1/58901958924b2bc7e0ffe898fb384926/asset-v1:LinuxFoundationX+LFS101x+2T2021+type@asset+block/tracerouterhel7.png)


### More Networking Tools ###

Now, let’s learn about some additional networking tools. Networking tools are very useful for monitoring and debugging network problems, such as network connectivity and network traffic.

Networking Tools 	  |  Description
--------------------- | --------------------------------
ethtool 	           | Queries network interfaces and can also set various parameters such as the speed
netstat 	           | Displays all active connections and routing tables; useful for monitoring performance and troubleshooting
nmap 	              |  Scans open ports on a network; important for security analysis
tcpdump 	           | Dumps network traffic for analysis
iptraf 	            |    Monitors network traffic in text mode
mtr 	               | Combines functionality of ping and traceroute and gives a continuously updated display
dig 	               | Tests DNS workings; a good replacement for host and nslookup

## Browsers, wget and curl ##

### Graphical and Non-Graphical Browsers ###

Browsers are used to retrieve, transmit, and explore information resources, usually on the World Wide Web. Linux users commonly use both graphical and non-graphical browser applications.

The common graphical browsers used in Linux are:

* Firefox
* Google Chrome
* Chromium
* Konqueror
* Opera

Sometimes, you either do not have a graphical environment to work in (or have reasons not to use it) but still need to access web resources. In such a case, you can use non-graphical browsers, such as the following:

Non-Graphical Browsers 	    |    Description
--------------------------- | --------------------------------------------------
lynx 	                      |  Configurable text-based web browser; the earliest such browser and still in use
elinks 	                    |    Based on Lynx; it can display tables and frames
w3m 	                       | Another text-based web browser with many features

### wget ###

Sometimes, you need to download files and information, but a browser is not the best choice, either because you want to download multiple files and/or directories, or you want to perform the action from a command line or a script. wget is a command line utility that can capably handle the following types of downloads:

* Large file downloads
* Recursive downloads, where a web page refers to other web pages and all are downloaded at once
* Password-required downloads
* Multiple file downloads.

To download a web page, you can simply type wget <url>, and then you can read the downloaded page as a local file using a graphical or non-graphical browser.

### curl ###
Besides downloading, you may want to obtain information about a URL, such as the source code being used. curl can be used from the command line or a script to read such information. curl also allows you to save the contents of a web page to a file, as does wget.

You can read a URL using curl <URL>. For example, if you want to read http://www.linuxfoundation.org, type curl http://www.linuxfoundation.org.

To get the contents of a web page and store it to a file, type curl -o saved.html http://www.mysite.com. The contents of the main index file at the website will be saved in saved.html.

![curl eg](https://courses.edx.org/assets/courseware/v1/f82c5e92a716627d3623a7cb1286613d/asset-v1:LinuxFoundationX+LFS101x+2T2021+type@asset+block/curlrhel7.png)


## Transferring Files ##

### FTP (File Transfer Protocol) ###

When you are connected to a network, you may need to transfer files from one machine to another. File Transfer Protocol (FTP) is a well-known and popular method for transferring files between computers using the Internet. This method is built on a client-server model. FTP can be used within a browser or with stand-alone client programs.

![ftp server](https://courses.edx.org/assets/courseware/v1/6c4efd743bc9707314f89c414e219e88/asset-v1:LinuxFoundationX+LFS101x+2T2021+type@asset+block/LFS01_ch11_screen33.jpg)

FTP is one of the oldest methods of network data transfer, dating back to the early 1970s. As such, it is considered inadequate for modern needs, as well as being intrinsically insecure. However, it is still in use and when security is not a concern (such as with so-called anonymous FTP) it can make sense. However, many websites, such as kernel.org, have abandoned its use.

### FTP Clients ###

FTP clients enable you to transfer files with remote computers using the FTP protocol. These clients can be either graphical or command line tools. Filezilla, for example, allows use of the drag-and-drop approach to transfer files between hosts. All web browsers support FTP, all you have to do is give a URL like ftp://ftp.kernel.org where the usual http:// becomes ftp://.

Some command line FTP clients are:

* ftp
* sftp
* ncftp
* yafc (Yet Another FTP Client).

FTP has fallen into disfavor on modern systems, as it is intrinsically insecure, since passwords are user credentials that can be transmitted without encryption and are thus prone to interception. Thus, it was removed in favor of using rsync and web browser https access for example. As an alternative, sftp is a very secure mode of connection, which uses the Secure Shell (ssh) protocol, which we will discuss shortly. sftp encrypts its data and thus sensitive information is transmitted more securely. However, it does not work with so-called anonymous FTP (guest user credentials).

![ftp image](https://courses.edx.org/assets/courseware/v1/0daf82fa22922b50848d2d73df3cfa1c/asset-v1:LinuxFoundationX+LFS101x+2T2021+type@asset+block/LFS01_ch11_screen34.jpg)

### SSH: Executing Commands Remotely ###

Secure Shell (SSH) is a cryptographic network protocol used for secure data communication. It is also used for remote services and other secure services between two devices on the network and is very useful for administering systems which are not easily available to physically work on, but to which you have remote access.

![ssh image](https://courses.edx.org/assets/courseware/v1/b19e7547d1f707f6ba4b134c31f43a31/asset-v1:LinuxFoundationX+LFS101x+2T2021+type@asset+block/LFS01_ch11_screen37.jpg)

To login to a remote system using your same user name you can just type ssh some_system and press Enter. ssh then prompts you for the remote password. You can also configure ssh to securely allow your remote access without typing a password each time.

If you want to run as another user, you can do either ssh -l someone some_system or ssh someone@some_system. To run a command on a remote system via SSH, at the command prompt, you can type ssh some_system my_command.

### Copying Files Securely with scp ###

We can also move files securely using Secure Copy (scp) between two networked hosts. scp uses the SSH protocol for transferring data.

To copy a local file to a remote system, at the command prompt, type 

    scp <localfile> <user@remotesystem>:/home/user/ and press Enter.

You will receive a prompt for the remote password. You can also configure scp so that it does not prompt for a password for each transfer.

![scp image](https://courses.edx.org/assets/courseware/v1/83970c9d6a9a9462fe7463ada6b79e45/asset-v1:LinuxFoundationX+LFS101x+2T2021+type@asset+block/LFS01_ch11_screen38.jpg)

### Lab 14.1: Network Troubleshooting ###

Troubleshooting network problems is something that you will often encounter if you haven't already. We are going to practice some of the previously discussed tools, that can help you isolate, troubleshoot and fix problems in your network.

The solution file contains a step-by-step procedure for exercising many of the tools we have studied. Please repeat the steps, substituting your actual network interface names, alternative network addresses and web sites, etc.

 Suppose you need to perform an Internet search, but your web browser can not find google.com, saying the host is unknown. Let's proceed step by step to fix this.

1. First make certain your network is properly configured. If your Ethernet device is up and running, running ifconfig should display something like: 

    student:/tmp> /sbin/ifconfig

    eno167777 Link encap:Ethernet  HWaddr 00:0C:29:BB:92:C2
          inet addr:192.168.1.14  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:febb:92c2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3244 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2006 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4343606 (4.1 Mb)  TX bytes:169082 (165.1 Kb)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 

On older systems you probably will see a less cryptic name than eno167777, like eth0, or for a wireless connection, you might see something like wlan0 or wlp3s0. You can also show your IP address with:

    student:/tmp> ip addr show

    1: lo:  mtu 65536 qdisc noqueue state UNKNOWN group default
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
    2: eno16777736:  mtu 1500 qdisc pfifo_fast state \
        UP group default qlen 1000
        link/ether 00:0c:29:bb:92:c2 brd ff:ff:ff:ff:ff:ff
    p    inet 192.168.1.14/24 brd 192.168.1.255 scope global dynamic eno16777736
            valid_lft 84941sec preferred_lft 84941sec
        inet 192.168.1.15/24 brd 192.168.1.255 scope global secondary dynamic eno16777736
            valid_lft 85909sec preferred_lft 85909sec
        inet6 fe80::20c:29ff:febb:92c2/64 scope link
            valid_lft forever preferred_lft forever

### Lab 14.2: Non-Graphical Browsers ###

There are times when a graphical browser is not available, but you need to look up or download a resource. In this exercise, we are going to experiment with using non-graphical web browsers.

The solution file contains a step-by-step procedure for exercising the tools discussed. Please repeat the steps, substituting web sites, etc.

We have discussed non-graphical browsers:
* lynx
* links and elinks
* w3m

There are times when you will not have a graphical window interface running on your Linux machine and you need to look something up on the web or download a driver (like a graphics driver in order to bring up a graphical window interface). So, it is a good idea to practice using a non-graphical web browser to do some work.

With links, you can use your mouse to click on the top line of the screen to get a menu. In this case, we want to go to google.com (or your favorite search engine), so you can just type g to go to a typed-in URL.

Pressing the TAB key will move your cursor to the OK button. You can then press the ENTER key.

You should now be at google.com (or your favorite search engine). Use the down-arrow key to move through the choices until you reach the blank line used to enter your search query. Now type Intel Linux graphics drivers in the search box. Use the down-arrow key to move you to the Google Search button. With that highlighted, press the ENTER key.

Use your down-arrow key to move to the entry: Intel(R) Graphics Drivers for Linux - Download Center. It may take several presses of the down-arrow key. You can press the space-bar to move down the page or the 'b' key to move back up the page if needed. Once this line is highlighted, press the ENTER key. You will now go to the Intel Graphics Driver for Linux page. If you want, you can read the page. Remember, the space-bar will page you down the page while the 'b' key will move you back up the page. The Page Down and Page Up keys will do the same thing if you prefer. Find the URL under the line

URL Location:     

Position your cursor at this line using the up-arrow or down-arrow key. Press the ENTER key to go to this location.

Page down this page until you see the line:

Latest Releases
      
If you move your cursor with the arrow keys, find the latest version (with the most recent release date) under this section. If using your arrow-keys, you should highlight Release Notes. Press the ENTER key.

This has installers for versions of Ubuntu and Fedora, along with the source code. You will need to page down a page or two depending on the size of your screen.

Select one of the installers, perhaps for the version of Linux that you are running, or just a random one, and press the ENTER key.

You should see a text dialog box with choices of what to do. Save the package wherever you want to.

You can now quit your non-graphical browser. If you used links, then click on the top line of the screen, select the File drop-down menu item, and click on Exit. Confirm that you really want to exit Links. You should now see your shell prompt. 

## Summary ##

### Chapter Summary ###

You have completed Chapter 14. Let’s summarize the key concepts covered:

* The IP (Internet Protocol) address is a unique logical network address that is assigned to a device on a network.
* IPv4 uses 32-bits for addresses and IPv6 uses 128-bits for addresses.
* Every IP address contains both a network and a host address field.
* There are five classes of network addresses available: A, B, C, D & E.
* DNS (Domain Name System) is used for converting Internet domain and host names to IP addresses.
* The ifconfig program is used to display current active network interfaces.
* The commands ip addr show and ip route show can be used to view IP address and routing information.
* You can use ping to check if the remote host is alive and responding.
* You can use the route utility program to manage IP routing.
* You can monitor and debug network problems using networking tools.
* Firefox, Google Chrome, Chromium, and Epiphany are the main graphical browsers used in Linux.
* Non-graphical or text browsers used in Linux are Lynx, Links, and w3m.
* You can use wget to download webpages.
* You can use curl to obtain information about URLs.
* FTP (File Transfer Protocol) is used to transfer files over a network.
* ftp, sftp, ncftp, and yafc are command line FTP clients used in Linux.
* You can use ssh to run commands on remote syste* 

