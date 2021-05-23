Date: <built-in method today of type object at 0x92ad20>
Author: Ayush Agrawal
Book: docker
Topic: "Docker Container " 


---


# Docker container Commands  

mainly docker has two parts  
* docker engine or server and this is main thing which handle all requests.   
* docker command line and this the bridge between engine and user.   


### Docker command systax  

docker < main command > < sub commands> (option)

### docker version   

Return  docker version which is install in your system.


### docker info   

most of the config values related to engine.


### docker container   

This is a main command to handle all requests related to container and we are goingt to use that to mainly handle all things we are going to handle for container.  

#### container run   

this command use to run docker containter in your system.  

__Options__   

* image name (required)   
* --publish / -p  --> to bind outside port with inside port.  
* --detach  --> detach container from command line.  
* --name --> name of container, if you did not provide one then docker provide by default ( mainly scientist or hacker name)   
* --env/ -e --> environment variable for contianer.  


#### container ls   

lsit of all running containner 


__Options__   

* -a --> all container running or not

#### container stop <Id>   

stop docker container whose Id is provided

#### container log < container name or id> 

provide logs for given container  

#### contianer top < container name or id >   

Provide all running process fot given container   

#### container rm < multiple id for removing contianer >   

This will remove all non running contianer by default.  


__Options__   

-f --> fource to remove running container   

#### docker start <name or Id of container>  

This command use to run continer which are already avilable in system.  

---

__Question__ What happen when you run docker run command?  

* Look for image in local cache   
* then look for remote image  
* download given version  
* create new container on basis of image  
* give a virtual IP on private network inside docker engine  
* then if you open any port it will look inot it and attach them.   
* then docker start runing CMD provide in docker file.  

---   

__Question__  Container VS virtual machine?  

Container are not mini VM's, they are like process.  

When you are running some thing in docker that thig run on your host there is not sepraet area of that as VM do.  

let run mongo in docker and run docker top to see all process running ther, then check in main host.  

---   

__Question__ Whats going inside container and how to check?  

There are mainly three type of commands in container to check whats going inside containter.  

* top  
* inspact 
* stats  

__top__  

this command help to see all process running for this contianer.  

__inspact__  

All metadata while setting up container and starting them.  

__stats__  
This comamnd provide all information related to performance for runnign container.  

----   

__Question__  How to get a shell in running contianer?

There are mainly two ways to get a shell dor docker container  
* use __-it__ in docker __run__ command.  
* use docker __exec -it__ command   

There is no need of SSH specilly   

- run -it -  
this is help to provide tty and intrect with it.  
you can also pass command which run when container start after image name but that override defalt command provided by image.  

like nginx provide by default command to run nginx demon in container.

run -it --name nginx nginx bash  

this opne and bash shell inside containr but now nginx did not run as you override default command.  

if you want to start a container and open shell then use __ai__ opeitons.   

- docker continer exec -it <name> command   
that open a new bash in existing running contianer.  

