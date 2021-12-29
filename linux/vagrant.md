VAGRANT
=======



## Vagrant with libvirt 

[Vagrant libvirt](https://github.com/vagrant-libvirt/vagrant-libvirt)

command file $HOME/vagrant 

```
#!/bin/bash
podman run -it --rm \
 --group-add keep-groups \
 -e LIBVIRT_DEFAULT_URI \
 -v /var/run/libvirt/:/var/run/libvirt/ \
 -v ~/.vagrant.d/boxes:/vagrant/boxes \
 -v ~/.vagrant.d/data:/vagrant/data \
 -v ~/.vagrant.d/data:/vagrant/tmp \
 -v $(realpath "${PWD}"):${PWD} \
 -w $(realpath "${PWD}") \
 --network host \
 --entrypoint /bin/bash \
 --security-opt label=disable \
 docker.io/vagrantlibvirt/vagrant-libvirt:latest \
 vagrant $@
```

## Vagrant boxes

[KVM boxes](https://app.vagrantup.com/boxes/search?provider=libvirt)