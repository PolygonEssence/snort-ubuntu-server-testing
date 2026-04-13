# [Windows 10]Setup Ubuntu Server VM 24.04.4 in Virtualbox and Establish A Connection to Home Network + Private Network

# Prerequisites: 

* [Ubuntu Server 24.04.4 LTS ISO](https://ubuntu.com/download/server/thank-you?version=24.04.4&architecture=amd64&lts=true) (Download will start automatically.)
* [VirtualBox 7.6.2 r172322 (Qt6.8.0 on Windows) for Windows Hosts](https://download.virtualbox.org/virtualbox/7.2.6/VirtualBox-7.2.6a-172322-Win.exe) (Download will start automatically.)
* A strong and working internet connection on the Host device.
* A private home network.
* 12Gb+ (Reccomended: 16Gb+) of RAM on the Host device.

**If your setup is not exactly as follows [here](./walkthrough.md), you will probably have issues. Please refer to the [FAQ](./faq.md)**
# Completed with the following Host Device Specifications:
~~~
Edition	Windows 10 Home
Version	22H2
Installed on	‎4/‎8/‎2024
OS Build	19045.6466

Device Name	DESKTOP-1L23R6N
Processor	Intel(R) Core(TM) i7-9700K CPU @ 3.60GHz   3.60 GHz
Installed RAM	16.0 GB
Storage	233 GB SSD Samsung SSD 860 EVO 250GB, 1.82 TB HDD ST2000DM008-2FR102, 932 GB HDD TOSHIBA MQ01ABD100
Graphics Card	NVIDIA GeForce GTX 1660 SUPER (6 GB)
Device ID	241F13F1-C24A-4614-B5EF-F9E418997D81
Product ID	00326-10000-00000-AA069
System Type	64-bit operating system, x64-based processor
Pen and touch	No pen or touch input is available for this display
~~~

# A note on supplying resources to the VM
In an experiment, I approximately halved the resources I used for set up. My RAM was 4096Gb, and I used  4 CPU Cores. This did not make a huge difference in setup time, and in fact the biggest factor in how long it will take to install Ubuntu Server 24.04.4 LTS is your Network strength. 

<img width="163" height="91" alt="Terrible-Download-Speed" src="https://github.com/user-attachments/assets/02c78151-6db7-4a1a-a90b-5dd1cfbf4902" />

~~~
At this download speed it might take at least a day just to download 1Gb of data.
~~~

~~~
Subnet: 192.168.56.0/24
IP: 192.168.56.244
Gateway: Blank
Name Server: Blank
~~~
