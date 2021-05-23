Date: <built-in method today of type object at 0x92ad20>
Author: Ayush Agrawal
Book: docker
Topic: "Docker network"   


---

container port <name ofcontainer>  
container inspect --format '{{.NetworkSetting.IPAddress }}' <name for container>  

command one use for finding all ports connected to containers.    
second command use to search (--format) contianer config file and find details from there.   

you can create your own networks too.   

there is a network __host__ which skip docker network and connect direct to host

__Question__   Ip of a container is not same as IP of Host?

when you create any container it connect with a virtual network known as bridge or docker0 so it become a different network.   
if we want to coonect that virtual network to main network we use __-p__ opotion.  
any container you create connect by default to docker0 so they can communicate between them.   

---   

* docker network ls  
* docker network inspect  
* docker network create --driver    
* docker network connect    
* docker network disconnect    


__network ls__  

list all networks.   

__network inspect <network name>__  

this will provide alll containers attached  to that network.   

__network create <name>__   

create network by default driver bridge.  

NOTE:: you can use --network to provide to which network you connect.  

__netwok connect <network name>__  

to connect a particular network.  

__netwok disconnect <network name>__  

to disconnect a particular network.  

---   

__Question__  Docker DNS and how container find each other ?   

Name is very important as there is no static IP Address so we relie on DNS and docker use nameing.   

requied they are in same network.  

Default bridge did not have DNS build in you require to ue __--link__ while run command.   


