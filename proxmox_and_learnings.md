
# Day 1:


## We had to shutdown -h now, as setting up the proxmox hostname from the installed one , is not direct.


## We pressed F2 repeatedly, depends on computer


## commands to check gateway, (this is done on the proxmox we install)

> 
> 
> ip route | grep default


## Do we have 2 subnets??


## Only 1, 255.255.255.0 (192.168.0.1 -> 255)


## Issues with installation of Proxmox


### We are trying this one, for the installation stuck after eif boot mode detected issue:

-   <https://forum.proxmox.com/threads/installation-stuck-right-after-efi-boot-mode-detected.129692/>


### We solved this issue by telling the Linux kernel to use the BIOS framebuffer, instead of the graphics driver

-   [nomodeset fix](https://www.reddit.com/r/Proxmox/comments/1bfk6tp/installing_proxmox_81_crashing_when_loading/)


### 


# Categories


## Nodes


### the physical thing that connects.


## Protocol


### TCP/IP


### HTTP


### FTP


## Topology


### Bus, star, ring, mesh & tree


## Service Provider Networks


## IP Address (not important)


## DNS


## Firewall


## NAT


# Links


## [Functional Proxmox Homelab Framework](https://medium.com/@liamcs98/functional-proxmox-homelab-framework-1bc7a68cc559)


## [I turned my old PC into a Proxmox-powered home lab – here's how it went](https://www.xda-developers.com/i-turned-my-old-pc-into-a-proxmox-home-lab/)


## [How to enable PCI passthrough in Proxmox?](https://www.xda-developers.com/enable-pci-passthrough-in-proxmox/)


## [Building a homelab with Proxmox](https://www.remotelycurious.net/post/homelab/)


### management IP address, is just an IP address so you manage a device directly, independent of gateway. Eg: for a switche


### Here the example is a gateway  with the mgmt address &#x2013;> 192.168.0.10/24 and the address  192.168.0.1


### The usual structure goes something like this

-   Datacenter:

    -   pve
    
        -   100 (pfsense)
        
        -   101 (centos-silverr)
        
        -   102 (centis-client)
        
        -   103 (centis-clone)
        
        -   1000 (centos-template)
        
        -   local (pve)
        
        -   local-lvm (pve)

-   local-lvm hlds VM disk images & local holds backups and ISO's


### NIC (Network Interface Cards) are listed as enp1s0, enp2s0, enp3s0, enp4s0, enp5s0, enp6s0


### A Linux Bridge does not need an IP address, but in this context we need it for management  (Eg: vmbr0)


### The vmbr0 us for the (WAN?). The vmbr1 is for the internal network segment, which is in need for its own Linux Bridge


### If we look at  /etc/network/interfaces, we will the six enp1s0&#x2026;etc&#x2026;


## [Main Page](https://pve.proxmox.com/wiki/Main_Page)


### More cool links like, Proxmox support of QEMU, KVM, and Linux containers


### How to migrate to Proxmox


## [How to Home Lab](https://www.dlford.io/series/how-to-home-lab/)


### --


## [pfSense](https://docs.netgate.com/pfsense/en/latest/)


### -


## [Basics of Computer Networking](https://www.geeksforgeeks.org/basics-computer-networking/)


### -


## [How to Install pfSense Software on Proxmox VE](https://www.zenarmor.com/docs/network-security-tutorials/how-to-install-pfsense-software-on-proxmox)


### 


## [Linux Foundation Bridge](https://wiki.linuxfoundation.org/networking/bridge)


### -


## [Linux Foundation Tunneling](https://wiki.linuxfoundation.org/networking/tunneling)


## [Arch Wiki Network Configuration](https://wiki.archlinux.org/title/Network_configuration)


## [Arch Wiki OpenVPN](https://wiki.archlinux.org/title/OpenVPN)


## [The Homelab Wiki Install and Setup Proxmox VE](https://thehomelab.wiki/books/promox-ve/page/install-and-setup-proxmox-ve)


## [I have no idea](https://forum.proxmox.com/threads/how-to-configure-proxmox-and-pfsense-vm-so-that-all-network-requests-go-through-pfsense.64021/)


## [netgate forum Homelab  and  pfSense](https://forum.netgate.com/topic/136758/homelab-pfsense)


## [Homelab overview](https://opensource.com/article/19/3/home-lab)


## [install pfsense as a vm](https://forum.proxmox.com/threads/install-pfsense-as-a-vm-on-proxmox-single-nic-manageable-physical-switch-vlans.121597/)


## [fsense with 1 NIC in homelab](https://forum.proxmox.com/threads/pfsense-with-1-nic-in-homelab.86031/)


## [LOTS of basic things, please READ](https://tldp.org/LDP/nag2/index.html)


### IP Addresses

-   IP Addresses are divided into classes. (Some allowing a handful of subnets, but lots of hosts per network, others MANY subnets but few hosts per network)

-   Reserved for private use

    -   10.0.0.0 through 10.255.255.255
    
    -   172.16.0.0 through 172.31.0.0
    
    -   192.168.0.0 through 192.168.255.0


### Firewalls are hosts that are connected to two or more networks, but don't route traffic between them.


## [debian basics, also 2ND IMPORTANT](https://www.debian.org/doc/manuals/debian-reference/ch05.en.html)


## [Understanding the Difference Between DNS Server and Gateway](https://www.browserscan.net/blog/dns-server-gateway/)


## [small stuff, difference DNS server, and gateway](https://networkengineering.stackexchange.com/questions/44742/why-do-routers-have-only-a-few-interfaces)


## [small, why do routers only have a few interfaces?](https://networkengineering.stackexchange.com/questions/44742/why-do-routers-have-only-a-few-interfaces)


## [network switch vs router](https://www.cloudflare.com/en-gb/learning/network-layer/what-is-a-network-switch/)


## [purpose of switch in home network](https://www.reddit.com/r/HomeNetworking/comments/xhrrgp/what_is_the_purpose_of_a_switch_in_a_home_network/)


### people often have more devices than the ports their routers have


### unmanaged switches


### managed switches

-   more features

-   commonly used &#x2014;> VLANS

    -   to talk with other VLAN-aware devices (isolated traffic)
    
    -   home &#x2013;> isolate IoT devices from network
    
    -   biz &#x2013;> separate bandwidth-sensitive IP-based telephones from normal traffic (to prioritize VOIP)

-   commonly used &#x2013;> LAGS (Link Aggression)

    -   multiple parallel paths to high speed devices
    
    -   NAS that gets used by multi clients. 2 or more ethernet cables between NAS and switch. spread user connections better, no sharing


## [best practical explanation of VLAN!](https://www.practicalnetworking.net/stand-alone/vlans/)


### VLAN allows a single switch to be multiple switches


### ![img](./proxmox_and_learnings/VLAN_1.png)


### A single switch will have multiple (Eg: 3) VLANS. So, each VLAN is a switch. And a VLAN is simply a number assigned to a switch port. (Eg: 1st port and 2nd port is assigned VLAN #10, followed by empty port 3, 4, and 5, 6 being VLAN #20).


### Perspective &#x2013;> we see 3 single frame arriving at the switch. But the switch sees 3 different frames arriving at 1 port at 1 VLAN, exiting at 1 port at the same VLAN


### In the MAC address table, each MAC line has a VLAN number. The total records have the effect of each VLAN having its own MAC address table.


### This understanding of each VLANS being independent of each other brings us to &#x2013;> VLANs allow you to extend you to EXTEND A SINGLE VIRTUAL SWITCH ACROSS MULTIPLE PHYSICAL SWITCHES

-   We understand from the illustration below, that VLAN #10 spans 2 physical switches

-   ![img](./proxmox_and_learnings/VLAN_2.png)

-   there are real placement benefits to this. One can have the same VLAN in different rooms (Layer 2 topology)

-   Each connected switch ports (note: CONNECTED) automatically is a member of a single VLAN. Its called Access port &#x2013;> switch port that is a member of 1 VLAN


### An Access port is a switch port that is a member of only 1 VLAN

-   Which brings  us next to a Trunk port


### A Trunk port is a switch port that carries traffic for multiple VLANs

-   Just needs  to configure several VLANs for that single port


### 


## [Wanna understand etc\_network\_interfaces and other configs](https://www.baeldung.com/linux/network-interface-configure)


### What happens in etc/network/interfaces (each line)

-   define an interface per line. (usually: interface namee, type, method)

-   define IP address, network mask, gateway

-   configure DNS server (1 line)

-   execute script after interface enabled (post-up), and others &#x2013; pre-down


### Sometimes, the etc/netork/interfaces is empty. Why?

-   becoz it might be managed by another tool (eg:network manager)

-   Solution: disable network manager

    > 
    > 
    > $ sudo systemctl stop NetworkManager.service
    > $ sudo systemctl disable NetworkManager.service


## [types of firewalls](https://www.paloaltonetworks.com/cyberpedia/types-of-firewalls)


### A common way to categorize is by placement within network, form factor,  the systems they protect


### Network firewall

-   between trusted and untrusted network, such as between internal and internet

-   ![img](./proxmox_and_learnings/firewall_1a.png)


### Host-Based Firewall

-   works on a device level. Basically the threats arrice at the device. Ensuring all other devices are protected. Very secure.

-   ![img](./proxmox_and_learnings/firewall_1b.png)


### The following are Firewall types by form factors


### Hardware Firewall

-   basically, a physical  device, independent of the host.

-   Its  proactive? But according to Linux, its a myth that harrdware firewalls are more secure.


### Software Firewall

-   same technology as hardware firewall

-   can even be deployed within virtualized networrk


### theres more-----------------


## <https://www.digitaltut.com/ppp-over-ethernet-pppoe-tutorial>


### Should I read this? I dont   know


## [Linux networking ELI5](https://medium.com/@tunacici7/linux-networking-eli5-part-1-networks-interfaces-b912826d699b)


### ---


## [Networking basic for sysadmin (REDHAT simp)](https://www.redhat.com/sysadmin/sysadmin-essentials-networking-basics)


### 

