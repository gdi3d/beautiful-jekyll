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
2. Spin up a container using the following command on your terminal
```
docker run -it --name myPythonContainer python:3.6 bash
```

