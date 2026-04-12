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

Start the Machine!
~~~
  ## 2. Setup & Install
  
**A.** Pre-Installation Setup  

~~~
Note: Use the Arrow Keys to navigate the following menus and [enter] or [space] to select.

1. Choose your language [English]
---If prompted for [Installer update available] Continue without updating---
2. [Keyboard Configuration] If you have an English QWERTY keyboard SKIP otherwise identify an alternative keyboard.
3. [Choose the type of installation] SKIP
4. [Network Configuration]
    Name   Type  NOTES
  [enp0s3  eth   -             >  ]
   DHCPv4 192.168.x.x/24
     [Your Network Adapter]

[enp0s8  eth   -               >  ]
   DHCPv4 192.168.56.104/24
     [Red Hat, Inc. / Virtio network device]

Highlight enp0s8 and select it, then select the IPv4 Method dropdown,
 and select "Manual," then fill in the following details:
  Subnet: 192.168.56.0/24
  Address: 192.168.56.244
Leave the rest of the options blank and "save," and "done."

5. [Proxy Configuration]
    Proxy address: Skip!

6. [Ubuntu archive mirror configuration]
    Verify -> Mirror address: http://us.archive.ubuntu.com/ubuntu/
      It will test the default address before continuing, if it fails try:
        https://mirrors.mit.edu/ubuntu/

7. [Guided storage configuration]
     Skip!

8. [Storage configuration]

  A. Highlight free space under "AVAILABLE DEVICES" and "Create Logical Volume."
  B. Create logical volume
  C. Create the following 5x mount points. Divide your free space by 4 and round down to the nearest
       multiple of 10. E.G 50 GB free / 4 = 12.5 -> 10 GB each mount point. Ignore the name!
  D.Verify you have each in any order:
    MOUNT POINT    SIZE      TYPE     DEVICE TYPE
    /boot          10G        -            -
    /home          10G        -            -
    /usr           10G        -            -  
    /var           10G        -            -
    SWAP            4G        -            -
  E. Continue, ignore the warning.

9. [Profile configuration]
    Your name, your server name, and username are up to you.
    [Password] Choose a secure password that is at least 8-12 characters long,
      uses symbols (!,?,_), and doesn't contain any spelled out words, or repeating characters.
      Write this password down and keep it in a secure environment!

10. [Upgrade to Ubuntu Pro]
      Skip!

11. [SSH Configuration]
    Skip!

12. [Featured server snaps]
    Skip!

13 [Installation]
    Congratulations! you have now set yourself up for success.
    Now you must only wait several hours for Ubuntu to install itself.
    If you need to step away DO not power off the machine or send the shut-down signal.
    Instead, save the machine state. File > Close > Save the machine state.
    Highly reccomended to leave it on when you are busy or not at your computer.
~~~

  ## 2. Post-Install Configuration
  
**A.** Final Stretch.

~~~
1. Login us your user then login as sudo, run |sudo -i| (without | | )
2. |apt update|
3. | apt upgrade -y|
4. |ip link| Verify enp0s8 has the IP of: 192.168.56.244 and there is PROMISC_UP.
5. |ip link enp0s8 promisc on| <--- Run this after every reboot.
6. |tcpdump -i enp0s8 -v|
7. tcpdump will now begin listening for traffic on your VM's private network and will output any traffic
   into the terminal.
8. Open a terminal on your Windows host and ping 192.168.56.244.
9. If everything goes well you should see several ICMP pings in the VM terminal. Otherwise, verify
   all setup is correct.
~~~

