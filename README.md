# Vagrant + CoreOS +  Fleet + Kubernetes + Docker Test Project

This demo tries to start INAETICS provisioning service and agents, it depends on a running docker-registry-service and docker-image-builder, see https://github.com/INAETICS
	 	
## Usage

### Start etcd and fleet cluster (clustersize = 1 in this test project ;) )

cd EtcdAndFleet  
vagrant up  
	- this starts CoreOS within Vagrant, running etcd and fleet, IP is 172.17.8.20  

### Start some cluster nodes

cd Cluster  
vagrant up  
	- this starts 5 CoreOS cluster nodes within Vagrant, running fleet with etcd on the EtcdAndFleet machine  

### Check status deploy units

cd EtcdAndFleet     
vagrant ssh  

fleetctl list-machines    
fleetctl list-units  

fleetctl start units/provision-8080.service
fleetctl start units/agent-9090.service
fleetctl start units/agent-9091.service

fleetctl destroy agent-9091

## TODO
