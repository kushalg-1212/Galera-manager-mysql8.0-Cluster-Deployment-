# Installing Galera Manager and Automatically Deploying Mysql 8.0 Galera Cluster in Multiple Hosts 

##### Provided thatt below is my Setup We will now Install Galera Manager and Deploy Mysql8.0 Cluster on 3 Nodes 
&nbsp;

```sh
Mysql1 192.168.1.102
Mysql2 192.168.1.103
Mysql3 192.168.1.104
Galera-Manager 192.168.1.105
```

Assuming All Servers are Fresh Installed Ubuntu 20.04 Servers 

```
apt update -y
apt install wget -y
wget https://galeracluster.com/galera-manager/gm-installer
chmod +x gm-installer
./gm-installer install
```

The gm installer will start an interactive shell and will ask for few options , please give informations accordingly . If you need SSL , please give gdm a domain name while installing instead of IP address , Point the Domain to the IP addrress and it will automatically install SSL certificates using LetsEncrypt 

Once the installation Finishes Please goto the IP address of Galera manager i.e for me http://192.168.1.105

&nbsp;


One the Main Screen Click on Add Cluster  

![](https://hackmd.io/_uploads/rkudzxA63.png)


Click on Deploy Cluster on user provided hosts 


Give it a name and select Appropriate host OS i.e ubuntu 20 and Click next 


![](https://hackmd.io/_uploads/r1QAfeCph.png)


The Galera manager needs root access to the host server i.e all mysql nodes we shall use so it will present a ssh key that we need to add to the host servers 

![](https://hackmd.io/_uploads/ryYNXx0p3.png)

Copy that key and paste it inside /root/.ssh/authorized_keys  , if the folder /root/.ssh is not present it create it 

```sh
mkdir /root/.ssh
nano /root/.ssh/authorized_keys 
```

Once key is pasted restart  ssh service using command 

```sh
service sshd restart
```

Click on I have added public key as shown in the picture below and click finish 

&nbsp;

![](https://hackmd.io/_uploads/r1_Rml063.png)


Click on the Cluster just Created and Then Select Add nodes 

![](https://hackmd.io/_uploads/r1AENgA62.png)

Give Node IP address and Check Access , if Access is fine then we can Deploy the cluster , Repeate to add as many nodes as you want 
