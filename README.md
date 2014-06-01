# Ping the vagrant box

```
ansible all \
-m ping \
-u vagrant \
--private-key ~/.vagrant.d/insecure_private_key
```
