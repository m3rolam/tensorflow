## Requirements

These instructions require the following software:

* Vagrant - https://www.vagrantup.com/downloads.html
* VirtualBox - https://www.virtualbox.org/wiki/Downloads

## Instructions

From the root directory run the following

```
	vagrant up
```

Once the above command finishes succesfully, connect to the kafka manager 
http://192.168.34.181:9000/

At the top click add cluster.

configure the following: 
* Cluster Name: enter a name
* Cluster zookeeper host: zookeeper:2181
* kafka version: 0.9.0.1 (Actual running version is 1.0.1) 
* check enable jmx polling
* check poll consumer information
* click save

## Useful Commands

removes the vagrant virtual machine 
```
	vagrant destroy
```

Shows all vagrant virtual machine deployments 
```
	vagrant global-status
```

SSH into the vagrant vm 
```
	vagrant ssh
```

SSH into docker containers in the vagrant vm 
```
	docker exec -it <container name> /bin/bash
```

Show running docker containers 
```
	docker ps
```



