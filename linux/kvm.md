KVM
===


##Tags

\#kvm,\#qemu,\#virsh



##Naming

Domain=Virtual machine



##List domains

- Active `virsh list `
- All included  inactive `virsh list --all`



##Start and stop domain

- to start `virsh start {domain} `
- to power off `virsh destroy {domain} `



##Getting interfaces mac and ip address 

- Obtain interfaces and mac address `virsh domiflist {domain} `
- If the guest os is working in network , it's possible to obtain ip address from host arp table ` arp -e | grep {mac} `
