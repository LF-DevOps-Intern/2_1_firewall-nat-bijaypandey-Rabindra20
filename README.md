1. Create a virtual machine having the os centos.<br/>
a.Install firewall in the vm(centos might have firewall installed in default).(firewalld or iptables)<br/>
b.Block certain ip range/subnet using firewalld.<br/>
c.Allow http, https and ssh connection using firewall.<br/>
d.You can add other rules as well as you prefer.<br/>
    Note: The firewall rules should be saved permanently.<br/>

2. Create one vm with 2 network interfaces one should behave as WAN and another as LAN. Create another vm attaching the previously created LAN interface to it. <br/>
Implement NAT in the first vm, so that the second vm can access the internet.<br/>
Note: Configure the first vm as a router, so make the LAN interfaces in the first vm as gateway to the LAN network. And in the second vm configure the gateway to the ip of the first vm LAN ip.
