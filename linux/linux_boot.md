Linux boot
==========

based on centos 7

# Tags

\#grub,\#systemd


# Modify kernel startup parameters in grub 2

- Edit file */etc/default/grub* (or by the symbolink link */etc/sysconfig/grub*)

- Refresh grub configuration file `grub2-mkconfig -o /boot/grub2/grub.cfg`


# Some parameters

- *user_namespace.enable=1*  enable user namespaces



# Systemd

Default scripts are stored into */usr/lib/systemd*, customizations int */etc/systemd*



# Customize a service

- Copy the service file \*.service from */usr/lib/systemd/system* to */etc/systemd/service*

- reload systemd configurations `systemctl daemon-reload`



# Targets

Target it's a collection of services. COnfiugration is stored in files *.target*

- *multi-user.target* Default target for nongraphical machines 
- *rescue.target* *emergency.target* in case of startup issues



# List targets

`systemctl list-units --type=target`



# Default target

To know which is the default target at boot `systemctl get-default`



# Change target during boot

At startup, in the grub menu 

- edit (by pressing e) 

- add to kernel parameters *systemd.unit=rescue.target* (to start with ressce target)

- press Ctrl-X



# Enable service for autostart

Required services for a target are stored into /etc/systemd/system/{target}.target.wants

To enable a service to autostart `systemctl enable {service} `; It create a link on the configured in *install/WantedBy* parameter)


