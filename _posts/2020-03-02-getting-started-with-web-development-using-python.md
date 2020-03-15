---
layout: post
published: false
title: Quit Virtualenv and use Docker
---
Don't get me wrong, I really like [virtualenv](virtualenv.pypa.io "virtualenv.pypa.io") and it's pretty usefull in some scenarios. But sometimes you have to deal with OS dependendencies and that forces you to install new packages and it can get a bit messy in some scenarios.

If you haven't heard about Docker (containers), you could read about it at [https://www.tutorialspoint.com/docker/index.htm](https://www.tutorialspoint.com/docker/index.htm)

You can think of docker as a ***micro vm*** without all the overhead of a [Virtual Machine](https://www.tutorialspoint.com/ubuntu/ubuntu_virtual_machines.htm). 

Docker and other containers technologies are based on [LXC](https://linuxcontainers.org/). 

When you launch a container, just like a VM, you can choose what OS you want and you can pre-install software on it or use a public image already created by others.

The good part is that you can spin up a container, do your tests, run your code and then turn it off and forget about it and you don't need to install any dependencies on your OS for your code.

There's a lot of benefits of using containers on a production environment, but I'm not going to get into that in this post. If you want to know more about that make sure you read about 
- Kubernetes  
  [https://kubernetes.io/](https://kubernetes.io/)  
  [https://www.tutorialspoint.com/kubernetes/index.htm](https://www.tutorialspoint.com/kubernetes/index.htm)
- Docker Swarm  
  [https://docs.docker.com/engine/swarm/](https://docs.docker.com/engine/swarm/)  
  
# Getting Started
1. Install docker on your system https://docs.docker.com/install/
2. Spin up a container and access to it using the following command on your terminal
[![asciicast](https://asciinema.org/a/DZPuoKziGYC6nt3xiji1JzqKs.svg)](https://asciinema.org/a/DZPuoKziGYC6nt3xiji1JzqKs)
```
docker run -it --name myPythonContainer python:3.6 bash
```

Let's break down that command:
1. **docker** the cli
2 **run** runs a command inside a container (our command will be **bash**) https://docs.docker.com/engine/reference/commandline/run/
3. **-it** this flags means:
    - **i** Keep STDIN open even if not attached
    - **t** Allocate a pseudo-TTY
4. **--name** Gives your container a frendly name. In our case is **myPythonContainer** You can ommit it and docker will generate one for you
5. **python:3.6** here we're telling docker to use an image called **python** with the tag **3.6** 


That's it....! now you have python running inside a container, but this is not very usefull right?.

We need to be able to do a few things

1. Run your code inside that container
2. Open a port to expose your web application
3. Pass secrets using environment variables


### Run your code inside that container