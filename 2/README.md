2. Create one vm with 2 network interfaces one should behave as WAN and another as LAN. Create another vm attaching the previously created LAN interface to it. <br/>
Implement NAT in the first vm, so that the second vm can access the internet.<br/>
Note: Configure the first vm as a router, so make the LAN interfaces in the first vm as gateway to the LAN network. And in the second vm configure the gateway to the ip of the first vm LAN ip.<br/>

Steps:
-ip a 
-Ifcfg -ens33
-Ifcfg-ens37
-![uuidgen](https://user-images.githubusercontent.com/53372486/140005201-bbb8f528-2429-440e-a76c-ab8f02b89b44.png)<br/>
![2 ip](https://user-images.githubusercontent.com/53372486/140005211-ec9c64b6-4cc4-488e-b76e-590cf812efd8.png)
-sysctl -w net.ipv4.ip_forward=1 
-vi /etc/sysctl.d/ip_forward.conf
-firewall-cmd --permanent --direct --passthrough ipv4 -t nat -I POSTROUTING -o enp0s3 -j MASQUERADE -s enp0s8