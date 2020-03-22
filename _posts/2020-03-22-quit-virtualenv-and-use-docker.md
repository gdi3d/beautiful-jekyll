---
layout: post
published: true
title: Quit Virtualenv and use Docker
date: '2020-03-22'
Tags: 'beginner, docker'
subtitle: Start using docker in your dev environment
category: Posts
tags: beginner docker python
bigimg: /img/business-commerce-container-export-379964.jpg
---
Don't get me wrong, I really like [virtualenv](virtualenv.pypa.io "virtualenv.pypa.io") and it's pretty useful in some scenarios. But sometimes you have to deal with OS dependencies and that forces you to install new packages and it can get a bit messy in some scenarios.

If you haven't heard about Docker (containers), you could read about it at [https://www.tutorialspoint.com/docker/index.htm](https://www.tutorialspoint.com/docker/index.htm)

You can think of docker as a ***micro vm*** without all the overhead of a [Virtual Machine](https://www.tutorialspoint.com/ubuntu/ubuntu_virtual_machines.htm). 

# Launching your first Docker container

1. Install docker on your system https://docs.docker.com/install/
2. Clone the repo with the app I created for this

    ```
    git clone git@github.com:gdi3d/quit-virtualenv-use-docker.git
    ```
    
2. Spin up a container and access to it using the following command on your terminal
  
   ```
   docker run -it --name myPythonContainer --volume $(PWD):/code -p 8080:5000 python:3.6 bash
   ```
   
3. Install our python application requirements  
    
    ```
    cd /code
    pip install -r requirements.txt
    ```
4. Run the application  
    
    ```
    python main.py
    ```
5. Try to access our application from outside the container by opening a new terminal 
    
    ```
    curl http://127.0.0.1:8080/
    ```
It should return a **Hello**
6. You can also check the container is running using `docker ps`. This command will list all the container running.

    ```
    CONTAINER ID  IMAGE       COMMAND  CREATED         STATUS         PORTS                   NAMES
    989f00e4a7fc  python:3.6  "bash"   50 seconds ago  Up 10 seconds  0.0.0.0:8080->5000/tcp  myPythonContainer
    ```

7. Great!, now go back to the terminal where you have the container and close it First **ctrl+c** to shutdown the python process and then type `exit` to exit the container
8. You can check that the container is no longer running by typing
    
    ```
    docker ps
    ```

Here are the videos for these steps

Part 1
<script id="asciicast-Fy0X3UnBSIJNjqzzkc8tBDUrW" src="https://asciinema.org/a/Fy0X3UnBSIJNjqzzkc8tBDUrW.js" async></script>

Part 2
<script id="asciicast-0rN0Rcd4tp2ULRHMH9zUyz8tV" src="https://asciinema.org/a/NaeBsC0xKSQUOyPP3QHJ1qF0d.js" async></script>

# Creating a custom docker image 

Let's build a custom image for our application.

### Why?

By creating a custom image we can have ready-to-go container with all the things that we need for our application to run and also set the command to run when our container start.

First, let's create a file named **[Dockerfile](https://docs.docker.com/engine/reference/builder/)** in our application folder 

```
# Our custom new image is based on a public image of python 3.6
FROM python:3.6
# create the directory /code and set it as the working directory
WORKDIR /code
# Copy the files to the docker folder /code
COPY . /code
# Install the python packages that we need
RUN pip install -r requirements.txt
# Define what command should be executed when this container starts
ENTRYPOINT ["python", "/code/main.py"]
```

Now we need to [build](https://docs.docker.com/engine/reference/commandline/build/) the image:

```
docker build -t mydockerimage:latest .
```
It will output something like this:

```
Sending build context to Docker daemon  4.096kB
Step 1/5 : FROM python:3.6
 ---> 1daf62e8cab5
Step 2/5 : WORKDIR /code
 ---> Using cache
 ---> 246ac5eb5a44
Step 3/5 : COPY . /code
 ---> Using cache
 ---> 8ab217175a34
Step 4/5 : RUN pip install -r requirements.txt
 ---> Using cache
 ---> ff9500f71963
Step 5/5 : ENTRYPOINT ["python", "/code/main.py"]
 ---> Using cache
 ---> 8f765333673a
Successfully built 8f765333673a
Successfully tagged mydockerimage:latest
```

The `-t` flag tells docker to build an image with the name `myDockerImage`, the `:`indicates a version for our image (you could also use v1.1, v1.2,... for ex.) and the `.` indicates that the `Dockerfile` file is in the current directory.

This image now has everything that we need to keep developing our application. 

Let's run the container again:

1. First, delete the older container. Although we've already exited and it's not running there's still a container with the name **myPythonContainer** and you need to delete it to launch a new one with the same name.

    ```
    docker ps -a
    ```
    
    will list all the container, even the ones that are terminated:
    
    ```
    CONTAINER ID  IMAGE       COMMAND  CREATED       STATUS                    PORTS  NAMES
    989f00e4a7fc  python:3.6  "bash"   20 hours ago  Exited (0) 3 seconds ago         myPythonContainer
    ```
    
    ```
    docker rm myPythonContainer
    ```
2. Run our new container

    ```
    docker run -d --name myPythonContainer --volume $(PWD):/code -p 8080:5000 mydockerimage
    ```
    Notice the changes in this command compared with the first we used to launch our first container:
    - You will see a response with and ID like **5d82484a63134dc911e8d2184a881950817b5d8bd07d7a64e1ee1b8207394ef9** that's the ID of your container and it indicates that it has been launched.
    - Not using **-it**. We're using **-d**, that means that we run the container in the background.
    - Not using the image **python:3.6**, we're now using our new custom image **mydockerimage**
    - Not using an explicit command anymore. This is because we've already set that in our Dockerfile in the line `ENTRYPOINT ["python", "/code/main.py"]`
3. One thing you might notice is that we don't longer see what's happening inside the container. To be able to see what's going on inside the docker you can always use

    ```
    docker logs -f myPythonContainer
    ``` 
4. Open a new terminal and call our endpoint

    ```
    curl http://127.0.0.1:8080/
    ```
5. Go to the terminal where the `docker logs -f myPythonContainer` is running and you will see the call you just made.

Video
<script id="asciicast-cIMqUv6zfbDgrBOo5YLEPy99I" src="https://asciinema.org/a/cIMqUv6zfbDgrBOo5YLEPy99I.js" async></script>
    

That's it!, now you can use Docker while developing and keep your OS untouched.

# A bit more about containers

Docker and other containers technologies are based on [LXC](https://linuxcontainers.org/). 

When you launch a container, just like a VM, you can choose what OS you want and you can pre-install software on it or use a public image already created by others.

The good part is that you can spin up a container, do your tests, run your code and then turn it off and forget about it and you don't need to install any dependencies on your OS for your code.

There's a lot of benefits of using containers on a production environment, but I'm not going to get into that in this post. If you want to know more about that make sure you read about 
- Kubernetes  
  [https://kubernetes.io/](https://kubernetes.io/)  
  [https://www.tutorialspoint.com/kubernetes/index.htm](https://www.tutorialspoint.com/kubernetes/index.htm)
- Docker Swarm  
  [https://docs.docker.com/engine/swarm/](https://docs.docker.com/engine/swarm/)  
  
*Photo Credit: https://instagram.com/hikaique*