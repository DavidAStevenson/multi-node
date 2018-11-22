# multi-node
This is a simple multi-machine Vagrantfile.

It's useful in order to test provisioning tools such as Ansible and Chef, where you really need one machine to work from, and other machines to provision.

Nodes are assigned private-network IP addresses 192.168.31.10 and higher.
Adjust NODE_COUNT env var in Vagrantfile to change the number of nodes.

Bring up the multi-machine environment
```
vagrant up
```

Connect to the primary machine
```
vagrant ssh
```

Establish ssh connectivity from the primary machine to other nodes

```
[vagrant@master ~]$ ssh-keygen
...
[vagrant@master ~]$ ssh-copy-id -i /home/vagrant/.ssh/id_rsa.pub vagrant@192.168.33.11
...
[vagrant@master ~]$ ssh 192.168.33.11
[vagrant@node1 ~]$
```

