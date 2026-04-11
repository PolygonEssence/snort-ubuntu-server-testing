# [Full-Walkthrough] [Windows 10] (WIP) Setup Ubuntu Server VM 24.04.4 in Virtualbox and Establish A Connection to Home Network + Private Network

  ## 💡 <b>Assuming you've fulfilled the [pre-requisites here](./README.md) you may begin to open Virtualbox and follow the installation steps. 💡</b>


  For the graphical guide refer to [this page.](./walkthrough-graphical.md)  
  ## 1. Initial VM Creation


**A.** New Virtual Machine  
~~~
VM Name: Ubuntu Server 24.04.4 LTS
VM Folder: C:\Users\YourUserName\Virtualbox VMs
ISO Image: C:\Users\YourUserName\Downloads\ubuntu-24.04.4-live-server-adm64.iso [File path to ISO.]
OS Edition: (Skip)
OS: Linux
OS Distribution: Ubuntu
OS Version: Ubuntu (64-bit)
Proceed with Unnattended Installation: (Skip)
Set up unattended guest installation: (Skip)
Specify Virtual Hardware:
  4-8Gb or 1/2 of your Host Machine's RAM.
  4-8 Cores or 1/2 of your Host Machine's # of cores.
Specify Virtual Hard Disk:
  Create a New Virtual Hard Disk
    Hard Disk File Location and Size:
      C:\Users\....vdi(Choose somewhere with at least 50Gb free. Reccomended: 100Gb Disk Size.)
Hard Disk File Type and Format:
VDI(Virtual Disk Image)
[ ] Pre-allocate Full Size (Optional, reccomended if you have a large capacity drive. 2tb+)
~~~

**B. Configure New Virtual Machine**
~~~
Settings -> Expert Mode
General (Skip)
System
  Acceleration
    Paravirtualization Interface: Default
    Hardware Virtualization Nested Paging: [X] Yes
Display
  Screen
    Video Memory: 16 MB (Above 16 MB is completely optional.)
Storage
  Devices
    Verify Ubuntu Server 24.04.4 LTS.vdi is attatched to Ubuntu Server 24.04.4 LTS.
    (If there is "--" next to "attached to" the storage is not correctly setup.)
Audio (Skip)
Network
  Adapter 1:
    Attatched to: Bridged Adapter
    Name: Intel(R) Dual Band Wireless-AC 8265 (YOUR Host device's network card name.)
    Adapter Type: Intel PRO/1000MT Desktop (82540EM)
    Promiscous Mode: Allow All

  Adapter 2: 
    Attached to: Host-only Adapter
    Virtualbox Host-Only Ethernet Adapter
    Adapter Type: Paravirtualized Network (virtio-net)
    Promiscuous Mode: Allow All
[Skip Everything Else]
  



~~~



  
# 1.After installation is done reboot and login when prompted then login with sudo -i then run apt update and then apt upgrade && yes and wait
# 2. ip addr verify enp0s8 reads "inet 192.168.56.244/24 brd 192.168.56.255" ands that enp0s3 reads "inet 192.168.1.X/24 metric 100 brd 192.168.1.255
# 3. turn promiscuous mode on for enp0s8 run "ip link set enp0s8 promisc on" verify with "ip link"
# 4. run tcpdump --version and verify output text matches screenshot




# 5 will use 4 mount points, divide "free space" amount by 4 and round down to nearest multiple of 10. e.g if you have 50gb free space 50 / 4 = 12.5 -> 10g to 4 of each mount point (/boot, home, usr, var) swap gets 2-4g(2 = good host hardware, 4g = bad host hardware, good hardware = 12gb+ alotted to VM, bad hardware = less than 12gb alotted)

