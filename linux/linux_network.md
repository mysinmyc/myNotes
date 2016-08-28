Linux network 
=============

Based on centos 7


# list interfaces and ip

`ip addr list`




# Firewalld

## Change permanently zone membership for an interface

- add to the file */etc/sysconfig/network-scripts/ifcfg-{profileName}* parameter *ZONE={zone}*

- restart network service `systemctl restart network`

- check firewall zones ` firewall-cmd --get-active-zones`




# Network manager

Configuration can be changed live by using *nmcli* or *nmtui*. 

Interfaces Configuration is stored in */etc/sysconfig/network-scripts/ifcfg-{profileName}*. Any change performed directly on files requires restart of network service  `systemctl restart network`



# Hostname

stored in */etc/hostname*

