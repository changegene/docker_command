# docker_command
useful docker commands

## install docker


## set mirror hub （net/http: TLS handshake timeout）
$ echo "DOCKER_OPTS=\"\$DOCKER_OPTS --registry-mirror=http://f2d6cb40.m.daocloud.io\"" | sudo tee -a /etc/default/docker  

$ sudo vi /etc/docker/daemon.json
###
{   
  "registry-mirrors": ["https://registry.docker-cn.com"]  
}
###

$ sudo service docker restart 

## docker conf
$ sudo groupadd docker    
$ sudo gpasswd -a ${USER} docker  
$ sudo service docker restart   
$ newgrp - docker 


## docker 

|  | command | 
| :- | :- | 
| outport image:        | sudo docker save -o motifbreakr.tar xfli/motifbreakr |
| import image:         | sudo docker load --input motifbreakr.tar             |
| pull image:           | docker pull <name>                                   |
| show running docker:  | docker ps                                            |
| stop container:       | docker stop ID                                       |   
| show images:          | docker images                                        |
| delete images:        | docker rmi -f ID                                     |


## make docker images
###Dockerfile：  
FROM image_name:tag                   define the basic image and version

MAINTAINER user_name                  define MAINTAINER

ENV key value                         define ENV (you can set multi lines)

RUN command                           the command you need docker to do(you can set multi lines) 

ADD source_dir/file dest_dir/file	    Add the files from host machine to the docker, compressed file will be uncompress automatically  

CPOY source_dir/file dest_dir/file	  same as ADD command，but don't compressed file will be uncompress automatically 

WORKDIR path_dir	                    set the WORKDIR path  

EXPOSE port1 prot2	                  set the port expose from docker to host 

CMD argument	                        the commond execute after container run, it can be changed by "docker run argument"

ENTRYPOINT argument	                  same as CMD command，but it will not be changed by "docker run argument"  

VOLUME	                              mount host dir to the container
