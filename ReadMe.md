
### basic docker commands
docker build .  => build the image from the Dockerfile in the current directory 

docker run - p 3000: 3000  _container_id --rm => run the container with the given image id the - p means publish and 3000 on 3000 is the port i set up in the node man 

    --rm means remove the container after it stops, this is optional

    the first 3000 is the host port used to access the container

    the second 3000 is part of the exposed port where listening for

docker ps => list the running containers
docker stop _container_name => stop the container

docker xcommand --help => list all commands in that category 
docker --help => list all commands of docker

docker rm _container_name => remove the container

docker rmi _image_name => remove the image

docker images => list all images fetched or created linked to my hard drive

### interactive shell
docker run node => run the node image from ducker hub to add node to our container/create container with node installed

docker run -it node => expose an interactive session from our container to our hosting machine; can use node in terminal 

docker ps -a => list all containers including stopped ones

docker run -p 9000:9000 -d contain_id => the -d for detach mode runs in the background so terminals is still able to be used

docker run -it _containter_name => run the container in interactive mode best for when not having a port exposed and need terminal access

### change container name
Stop container
docker stop container_id

Remove container
docker rm container_id

Run again with custom name
docker run --name my_custom_name -d -p 9000:9000 image_id

### share to docker hub

make account with docker hub

docker login

docker tag local_image_id yourusername/repository_name:tag
ex:
docker tag b67a184f5bc7 yourusername/python-app:latest

docker push yourusername/repository_name:tag

docker pull yourusername/repository_name:tag

docker logout

.dockerignore  -> works like the .gitignore

### docker data movement

both these work, as build container with volume and run container with volume which will allow presistance of data

docker tag feedback-node:latest feedback-node:volumes
docker build -t feedback-node:volumes .

docker log => show logs of error to debug

bind mounts

docker run -d -p 3000:3000 --name feedback-app -v feedback:/app/feedback -v "/Users/path to directory:/app" feedback-node:volumes

Just a quick note: If you don't always want to copy and use the full path, you can use these shortcuts:

macOS / Linux: -v $(pwd):/app

Windows: -v "%cd%":/ap

### Network & how they interact
One container running your application code
Another container running your database
Perhaps a third container for a web server

Create a network:

docker network create my-network

List networks:

docker network ls

Connect containers to a network (when running):

docker run --network my-network --name container1 image1

docker run --network my-network --name container2 image2
Connect existing containers:

docker network connect my-network container1

docker network connect my-network container2
Disconnect from a network:

docker network disconnect my-network container1

Inspect network:

docker network inspect my-network

## docker compose

docker-compose up # runs file to make containers & images, -d for detach mode   
docker-compose down #shuts it down but does not remove volumes, -v to do it though

