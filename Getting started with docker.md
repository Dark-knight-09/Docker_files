Getting started with docker 

to check docker version
docker --version

to check docker info
-- docker info

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
> docker images ls

to remove a images in hub
> docker rmi [image_name]:[tag]

to pull a image from docker hub or repository(online)
> docker pull [image_name]:[tag]
> docker search [image_name] // search for image in docker hub

to rename the docker image in local hub
> docker tag [image_name]:[tag] [new_image_name]:[tag]

to push a image from docker hub or repository(online)
> docker push [account_name]/[container_image]

attach and deattach mode container
> docker run [image_name]:[tag] // attach deployement of the container  //acts as active log shell
> docker run -d [image_name]:[tag] //deattach deployment of the container command prompt or bash shell will be free

to stop docker container:
> docker stop [container_name]

to check logs in deattach container 
>docker logs [container_name]

for interactive deployment of container 
> docker run -i [image_name]:[tag]  //image will be de-actived after the shell session is exited.

for attachment to container terminal
> docker run -t [image_name]:[tag]
> docker run -it [image_name]:[tag]  //for interactive container terminal(*better option)

options
mapping internal port to external port
> -p  [host_port_no]:[external_port_no] // used when container want to communicate with host network or input from host. like accessing container deployed website
mapping host directory file for persistance storage of data
> -v  [external_directory_path]:[internal_directory_path]  

# data in docker container is ephemeral 

export environment variable to docker container
> docker run -e [variable_name]=[value]  [container_image]

to filter docker container using image name
> docker ps -a -f ancestor=[image_name] // search for all container with image name
> docker ps -a -q   // gives all continer id's in the system
> docker ps -a  -f name=[container_name] // search for all container with container name

to remove docker container or image :
> docker rm [container_name] // remove container
> docker rmi -f [image_name] // remove image
> docker rm $(docker ps -a -q -f name=[container_name]) // remove all container



steps to create Dockerfile 
1. > From [operating_system_image]      // import image
2. > WORKDIR /[NAME] // act as current working dir in container filesystem
3. > COPY [host_path_folder] [container/path]    // copying source code  folder to container
4. > RUN              // update apt repo
5. > RUN              // install dependecies using apt
6. > RUN              // install python lib using pip
7. > ENTRYPOINT or CMD       // declaring ENTRYPOINT or default command

NOTE:
1.ADD: used to copy file from host with additional functionality of downloading from internet and extract files.
converting Dockerfile to Dockerimage.
2. COPY: used to copy file from host to container.



name of the docker image should be in lowercase..
>docker build -t [account_id]/[image_name] [dockerfile_path] // account id not necessary 




// by default docker uses TCP connection to communicate with host or port mapping.
> docker run -p [host_port_no]:[container_port_no] \TCP or UDP\ [image_name]:[tag] 

Types of network in docker 
1. bridge(default)
2. none
3. host

docker newtorking commands
> docker  network [commands]
> Commands:
>  connect     Connect a container to a network
>  create      Create a network
>  disconnect  Disconnect a container from a network
>  inspect     Display detailed information on one or more networks
>  ls          List networks
>  prune       Remove all unused networks
>  rm          Remove one or more networks

Note: when containers are deployed they are deployed in bridge network by default.
> docker network ls // list all networks
> docker network inspect [network_name] // inspect network

ex:create a new bridge network
> docker network create  --driver=[newtork_type]  --subnet=[ip_addr] [network_name]

user defined bridge network containes Automatic service discovery (DNS resolution between containers), container names are automatically resolved to ip address. 

Note: Automatic service discover (DNS) is Not found in default bridge of containers across multiple host machines.

to deploy a container in AWS serverless environment (Elastic Beanstalk) follow the below steps
1. push the application docker image to docker hub through docker account.
2. while configuration of Elastic Beanstalk upload the "dockerrun.aws.json" file which docker image configuration.

