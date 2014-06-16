vagrant-test
============
## Versions
Ansible 1.6.2
Vagrant 1.6.3

## Ping the vagrant box

```
ansible all \
-m ping \
-u vagrant \
--private-key ~/.vagrant.d/insecure_private_key
```

## Enable provisioning with ansible

Add this to the Vagrantfile.

```
config.vm.provision :ansible do |ansible|
    ansible.playbook = "site.yml"
    ansible.inventory_path = "hosts"

    # After a breaking change in Vagrant 1.5 we must add
    # https://github.com/mitchellh/vagrant/issues/3096
    ansible.limit = 'all'
end
```

## Playbooks

### site.yml

Specifies that for the host 'vagrant' run the task called 'test connection' which just pings the VM.

```
---
- hosts: vagrant
  tasks:
    - name: test connection
      ping:
```

## Ansible configuration
Found in /etc/ansible/ansible.cfg

### Cowsay
Add ```nocows=1``` to turn off the cowsay output.

## Reading materials

* [Greate first tutorial](http://jamesdacosta.com/first-steps-with-vagrant-ansible-and-aws/)
* [Installing nodejs from Ubuntu ppa](http://www.geedew.com/2014/02/15/working-with-ansible/)
