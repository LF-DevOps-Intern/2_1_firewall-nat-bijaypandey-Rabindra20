1. Create a virtual machine having the os centos.<br/>
a.Install firewall in the vm(centos might have firewall installed in default).(firewalld or iptables)<br/>
Steps:<br/>
install<br/>
     yum install firewalld <br/>
     systemctl enable firewalld<br/>
checking state<br/>
     firewall-cmd –state <br/>
![firewall](https://user-images.githubusercontent.com/53372486/139917496-4f3c77c6-d99b-4ec2-af79-34b870a219c9.png)
----------------------------------<br/>
b.Block certain ip range/subnet using firewalld.<br/>
Steps:<br/>
block<br/>
-firewall-cmd --permanent --add-rich-rule="rule family='ipv4' source address='180.76.15.0/24' reject"<br/>
reload
-firewall-cmd –reload<br/>
![block ip](https://user-images.githubusercontent.com/53372486/139919969-a10c0735-6853-4fe1-b11c-f82f0ea18b33.png)

----------------------------------<br/>
c.Allow http, https and ssh connection using firewall.<br/>
Steps:
-firewall-cmd --zone=public --list-services<br/>
-firewall-cmd –zone=public–add-service=ssh --permanent<br/>
-firewall-cmd --zone=public –add-service=http --permanent<br/>
-firewall-cmd --reload<br/>
-firewall-cmd –zone=public --list-services<br/>
-firewall-cmd --zone=public –add-service=https --permanent<br/>
-firewall-cmd --reload<br/>
-firewall-cmd –zone=public --list-services<br/>
![services](https://user-images.githubusercontent.com/53372486/139921568-e1e61253-c693-4f1c-b694-c7aa9a6a3fd8.png)
----------------------------------<br/>
d.You can add other rules as well as you prefer.<br/>
    Note: The firewall rules should be saved permanently.<br/>
 Steps:<br/>
 -firewall-cmd --zone=public –add-port=4990-4999/udp --permanent <br/> 
 -firewall-cmd --reload<br/>
 -firewall-cmd –zone=public --list-all<br/>
    ![rule](https://user-images.githubusercontent.com/53372486/139922682-49616b70-a5d5-4d9b-b955-c22e6f04a23e.png)
----------------------------------<br/>