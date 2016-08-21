Linux boot
==========

based on centos 7


# Modify kernel startup parameters in grub 2

- Edit file */etc/sysconfig/grub*

- Refresh grub configuration file `grub2-mkconfig -o /boot/grub2/grub.cfg`


# Parameters

- *user_namespace.enable=1*  enable user namespaces