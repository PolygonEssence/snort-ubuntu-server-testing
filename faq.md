# Common issues and bug reporting.

1. I can't download any packages in my VM during the intitial installation or after in the terminal!
    A. Verify your VMs' network adapters #1 & #2 are **set-up as so:**


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
