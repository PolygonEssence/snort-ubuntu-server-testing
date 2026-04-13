# Common issues and bug reporting.
~~~
Please submit all bugs and issues to jakerivas127@gmail.com
~~~
  
## 1. Sudo, Sudo, Sudo! Make sure you're logged in as root or beginning commands with su!
   ~~~  
   sudo -i <-- Login as root
   su <-- prefix to run commands as root
   ~~~
  
  
## 2. I can't download any packages in my VM during the intitial installation or after in the terminal!
Verify your VMs' network adapters #1 & #2 are **set-up as so:**


| Adapter 1 | ENABLED |
| :--- | :--- |
| Attatched to | Bridged Adapter |
| Name | (YOUR Network Device) |
| Adapter Type | Intel PRO/1000 MT Desktop (8254|
| Promisuous Mode | Allow All |
| MAC Address | (Numbers) |
| Virtual Cable Connected | YES |

| Adapter 2 | ENABLED |
| :--- | :--- |
| Attatched to | Host-only Adapter |
| Name | Virtualbox Host-Only Ethernet Adapter |
| Adapter Type | Paravirtualized Network (virtio-net) |
| Promisuous Mode | Allow All |
| MAC Address | (Numbers) |
| Virtual Cable Connected | YES |

## 3. When I run tcpdump -i enp0s8 -v there isn't any input in the terminal!
If you're not seeing any ICMP pings when you run ping 192.165.56.244 from your Host try these commands 
to verify if tcpdump is receiving ANY traffic:
~~~
1. touch lab_ping.pcap
2. tcpdump -i enp0s8 -v -w lab_ping.pcap
3. Let run for a few minutes and execute multiple ping commands
4. Ctrl + C to cancel
5. tcpdump -r lab_ping.pcap
~~~
Find your host devices' IP/ ICMP pings, if there is none try #2!

## 4. WIP
