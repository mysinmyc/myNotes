KVM
===


## Tags

\#kvm,\#qemu,\#virsh



## Naming

Domain=Virtual machine



## List domains

- Active `virsh list `
- All included  inactive `virsh list --all`



## Start and stop domain

- to start `virsh start {domain} `
- to power off `virsh destroy {domain} `


## Huge pages for guest memory
- Add the following lines to /etc/syctl.d/20-huge.conf according to the memory (in this case 12GB) and group of libvirt group
```
vm.nr_hugepages=6144
vm.hugetlb_shm_group=36
```

- Insert in the domain config
```
  <memoryBacking>
    <hugepages/>
  </memoryBacking>
```

## Getting interfaces mac and ip address 

- Obtain interfaces and mac address `virsh domiflist {domain} `
- If the guest os is working in network , it's possible to obtain ip address from host arp table ` arp -e | grep {mac} `


## Resolve guest address from hypervisor

- install libnss-libvirt (on debian ` sudo apt install libnss-libvirt `)
- add to */etc/nsswitch.conf*
```
hosts:  ... libvirt_guest, ...* 
```

## Clone images

` virt-clone --auto-clone --original ${sourcevm} --name ${destvm} `



## Clone ubuntu guest

[Duplicate IP](https://kb.vmware.com/s/article/82229)

edit /etc/netplan/*.yaml

```
network:
  version: 2
  renderer: networkd
  ethernets:
    default:
      match:
        name: e*
      dhcp4: yes
      dhcp-identifier: mac
```