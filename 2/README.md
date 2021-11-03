2. Create one vm with 2 network interfaces one should behave as WAN and another as LAN. Create another vm attaching the previously created LAN interface to it. <br/>
Implement NAT in the first vm, so that the second vm can access the internet.<br/>
Note: Configure the first vm as a router, so make the LAN interfaces in the first vm as gateway to the LAN network. And in the second vm configure the gateway to the ip of the first vm LAN ip.<br/>
<br/>
Steps:<br/>
-ip a <br/>
-Ifcfg -enp0s3<br/>
-Ifcfg-enp0s8<br/>
<br/>
![nat](https://user-images.githubusercontent.com/53372486/140009807-3febfbad-8634-48f2-9960-bff25bd20725.png)
![host](https://user-images.githubusercontent.com/53372486/140009813-94f05cda-7164-428e-8eef-f6ec459d206f.png)


![boot](https://user-images.githubusercontent.com/53372486/140008339-4bdec54d-f990-4f14-9e5b-5e475b194a99.png)<br/>
<br/>

![ip  config](https://user-images.githubusercontent.com/53372486/140008346-38bc76c6-94c0-40d0-8fc3-501c0602a9bf.png) <br/>

-vi /etc/sysctl.d/ip_forward.conf
-net.ipv4.ip_forward=1
-sysctl -p /etc/sysctl.d/ip_forward.conf
-firewall-cmd --permanent --direct --passthrough ipv4 -t nat -I POSTROUTING -o enp0s3 -j MASQUERADE -s enp0s8
-route add default gw 192.168.1.0
-systemctl restart network-manager
