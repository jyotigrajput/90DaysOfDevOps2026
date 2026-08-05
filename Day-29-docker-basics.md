# What is Docker

--

## **What is a container and why do we need them?**
- Container is executable package of software which contain all the required things for ex. runtime, Dependencies, permission  to run an application
- Need -> to run the application platform independent (Solve `"works on my machine"` problem)

## Containers vs virtual machines what is real difference

| Containers           | Virtual Machines |
|:------------          | :-----------------|
| User Docker engine   | Use hypervisor | 
| use shared resources | use dedicated resource |
| Use Host OS          | Dedicate OS required |
| Resource utilization | resource wastage |
| Small in size        | Large in size |

## What is Docker architecture
- Docker Client - use to run docker command and communicate with dockerd(daemon) 
- Docker daemon - background process , wrapper to run contained command 
- Docker images -  blueprint (recipe)
- Docker container - running instance of image 
- Registry - Docker HUB

  
<img width="924" height="309" alt="image" src="https://github.com/user-attachments/assets/637f66ef-bd88-49cd-b6f2-f236fe34759a" />

## Install Docker

1. Install Docker on your machine (or use a cloud instance)
   - sudo apt-get update
   - sudo apt install docker.io
2. Verify the installation
   - docker version
3. Run the hello-world container
    -  docker search hello-world
    -  docker run hello-world
4. Read the output carefully — it explains what just happened
    - Search for hello-world image locally but doesn't found so download from docker Registry

## Run real containers
**1. Run an Nginx container and access it in your browser**
```
docker search nginx
docker run -p 80:80 -d --name nginx-demo nginx
```

`-p` -> publish port

`-d` -> background process

`80:80` -> first own system(pc/laptop port) : container port

`--name` -> give name to container

**2. Run an Ubuntu container in interactive mode — explore it like a mini Linux machine**
```
  docker run -it ubuntu bash
```
`-it` - interactive mode for ubuntu bash
**3. List all running containers**
```
  docker ps 
```
**4. List all containers (including stopped ones)**
```
  docker ps -a
```
**5. Stop and remove a container**
   ```
   docker stop <cotnainer-id>
   docker rm <container-id>
   docker rm <contianer-id > -f --> remove forcefully
   ```

## Explore
**1. Run a container in detached mode — what's different?**
    
    `docker run -d **image_name**`

**2.Give a container a custom name**
   
    `docker run --name **name** **image_name**`

**3.Map a port from the container to your host**  
  
    `docker run -p 80:80  **image_name**`

**4.Check logs of a running container**
    
     ` docker logs container_id`

**5.Run a command inside a running container**
     
     ` docker exec`
