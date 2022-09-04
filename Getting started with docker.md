Getting started with docker 

to check docker version
docker --version

to run sample container image in ur machine 
> docker run hello-world
-Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:  
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

to check running containers in dockers
 > docker ps //only running containers
 > docker ps -a //all contianers

to inspect the container 
>docker inspect [container_name]


to remove a container from local hub
> docker rm [contianer_name]

to check images in hub
> docker images

to remove a images in hub
> docker rmi [image_name]:[tag]

to pull a image from docker hub(online)
> docker pull [image_name]:[tag]

attach and deattach mode container
> docker run [image_name]:[tag] // attach deployement of the container 
> docker run -d [image_name]:[tag] //deattach deployment of the container command prompt or bash shell will be free

to check logs in deattach container 
>docker logs [container_name]

for interactive deployment of container 
> docker run -i [image_name]:[tag]

for attachment to container terminal
> docker run -t [image_name]:[tag]
> docker run -it [image_name]:[tag]  //for interactive container terminal(*better option)

options
> -p  [internal_port_no]:[external_port_no] //mapping internal port to external port
> -v  [external_directory_path]:[internal_directory_path]  //mapping host directory file for persistance storage of data

data in docker  is provisional

