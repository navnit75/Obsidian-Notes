## Process based Commands 
Killing process with partial name 
```
$ pkill -f <partial_name>
```

 Listing all the process 
```
$ ps -e 
```
## Package Based Commands 
Uninstalling Packages
```
$ sudo apt-get remove --purge oracle-java11-installer-local
```

Searching where are the Packages
```shell
$ whereis <package-name>
```

## Command for Debugging

Searching file in a directory and subs using name 
```shell
# find . -name <name of the file , can use wildcard > 
```

Search files for particular string 
```shell
# grep -rnw . -e "<string>"
```

## Networking Based commands 

List all the interfaces with IP addresses 
```shell
# ip -br -c addr show 
```

List all the interfaces with MAC addresses 
```shell
# ip -br -c link show
```

Adding IP address to the interface
```shell
# ip addr add 10.0.0.2/24 dev eth0
```

Deleting IP address to the interface
```shell
ip addr del 10.0.0.2/24 dev eth0
     OR
# ifconfig <interface name> 0.0.0.0
```

Restarting an network interface
```shell
# ip link set eth1 up
# ip link set eth1 down
```

Deletion of VLAN / interface 
```
# ip link delete <interface name> 
```

Changing the MAC address of an interface temporarily
```shell
sudo ifconfig <interface-name> down 
sudo ifconfig <interface-name> hw ether <new mac address>
sudo ifconfig <interface-name> up
```

Creating a vlan 
```shell
sudo ip link add link enp2s0 name enp2s0.5 type vlan id 5
sudo ip addr add 192.168.1.121/24 dev enp2s0.5 
sudo ip link set enp2s0.5 up
```

## Folder Operations Based Commands
Deleting a directory 
```shell
rm -rf dir1
```

To know the files type in the directory 
```
$ file *
```

To know the directory structure 
```shell
tree <dir-name>
```

## Routing Based Commands 
Adding a multicasting address
```
# route add -net 224.0.0.0/4 dev enp2s0
```

Adding an gateway for particular network 
```shell
# ip route add 192.168.10.0/24 via 192.168.5.1
```

Adding a default gateway 
```shell
# route add default gw <ip> 
```

## Accessing Remote PC

ssh access to a particular PC in the same network ( you need to know the password)
```
$ ssh <username>@<ip address> 
```

copying some file from this pc to another pc in same network 
```
$ scp [user@]SRC_HOST_IP:]file1 [user@]DEST_HOST_IP:]file2
```

Copying some folder from current PC to another PC in same network
```
$ scp -r [user@]SRC_HOST_IP:]file1 [user@]DEST_HOST_IP:]file2
```

## TC based General Commands

Knowing the status of QDISCS
```
$ tc  -s qdisc
```

## Utilities 

Installing the tomcat server
```
$ sudo apt install tomcat9 tomcat9-admin
```

Checking the status of tomcat server ( It should show 8080 )
```
$ ss -ltn
```

Disabling/Enabling tomcat
```
$ sudo systemctl enable tomcat9
$ sudo systemctl disable tomcat9
```

Installing default jdk 
```
$ sudo add-apt-repository ppa:linuxuprising/java

```

Stopping the apache service
```
Windows: 
Search > Services > apache tomcat > stop 
```

# Stopping the applications listening on given port 
```
Windows: 
netstat -o -n -a | findstr 0.0:8080
TCP    0.0.0.0:3000      0.0.0.0:0              LISTENING       3116

taskkill /F /PID 3116

LINUX: 
lsof -i :8080
kill $(lsof -t -i :8080)
```

## Ethtool Based Commands for NIC info

to know the Timestamping details regarding interface 
```shell
ethtool -T <interface name> 
```

to know the statistics of the interface
```shell
ethtool -S <interface name> 
```

to know if the port contains HW queues 
```
ethtool -l <interface_name>
```

to change the settings of queues in HW Queues. 
```
ethtool -L <interface_name> tx <number_of_queues> 
```

## Tar Based Commands 

Extracting the tar.gz in specific directory 
```shell
 tar -xvzf icon-j7200-icon-bam-dvw51.3-1-images_1.tar.gz -C ./navnit_extracted_images/
```

## Netstat Commands

To know the ports open for TCP connection 
```
netstat -anpl 
```