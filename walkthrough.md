# [Full-Walkthrough] [Windows 10] (WIP) Setup Ubuntu Server VM 24.04.4 in Virtualbox and Establish A Connection to Home Network + Private Network

  ## 💡 <b>Assuming you've fulfilled the [pre-requisites here](./README.md) you may begin to open Virtualbox and follow the installation steps. 💡</b>


  For the text-based guide refer to [this page.](./walkthrough.md)  
  ## 1. Initial VM Creation






# 1.After installation is done reboot and login when prompted then login with sudo -i then run apt update and then apt upgrade && yes and wait
# 2. ip addr verify enp0s8 reads "inet 192.168.56.244/24 brd 192.168.56.255" ands that enp0s3 reads "inet 192.168.1.X/24 metric 100 brd 192.168.1.255
# 3. turn promiscuous mode on for enp0s8 run "ip link set enp0s8 promisc on" verify with "ip link"
# 4. run tcpdump --version and verify output text matches screenshot




# 5 will use 4 mount points, divide "free space" amount by 4 and round down to nearest multiple of 10. e.g if you have 50gb free space 50 / 4 = 12.5 -> 10g to 4 of each mount point (/boot, home, usr, var) swap gets 2-4g(2 = good host hardware, 4g = bad host hardware, good hardware = 12gb+ alotted to VM, bad hardware = less than 12gb alotted)

