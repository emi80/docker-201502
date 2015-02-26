# Docker tutorial

In the following tutorial we are going to play around with some Docker comands. For the purpose, we use an Ubuntu virtual machine with Docker up and running and some already installed images.

## Start the virtual machine

Open a terminal and boot up the virtual machine:

```
$ cd crg-course
$ vagrant up
```

If everything goes fine you can now ssh into the machine:

```
$ vagran ssh
Welcome to Ubuntu 14.04.1 LTS (GNU/Linux 3.13.0-43-generic x86_64)
...
vagrant@vagrant-ubuntu-trusty-64:~$
```

## Useful commands
Here is a series of some useful Docker commands. Please check [Docker documentation](https://docs.docker.com/reference/commandline/cli/) for the complete list.

#### Check downloaded images

```
$ docker images
```

#### Search the Docker hub

```
$ docker search grape
```

#### Download images from the Docker hub

```
$ docker pull debian
```

#### Run a contatiner
The ``run`` command will create and start a container based on the specified image.

```
$ docker run debian env
```

#### List containers
The ``ps`` command output a list of running containers. 

```
$ docker ps
````

To get the list of all (running and non-running) containers use the ``-a`` option:

```
$ docker ps -a
```

If you only want to see container ids you can use the ``-q`` option:

```
$ docker ps -q
```

To get the id of the latest executed container:

```
$ docker ps -l -q
```

#### Remove containers
The ``rm`` command is used to remove Docker containers. Running containers cannot be removed unless ``-f`` option is used.

```
$ docker rm <container_id>
```

Using the ``ps`` command with ``-a`` and ``-q`` options is very usefull when you want to cleanup non-running containers:
```
$ docker rm $(docker ps -a -q)
```

#### Remove images

```
$ docker rmi <image_id>
```

## Create images

### Interactive mode

```
$ docker run -t -i debian
root@43270a6545e8:/# apt -get update
root@43270a6545e8:/# apt -get install samtools
root@43270a6545e8:/# exit
$ docker ps -l
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                     PORTS               NAMES
43270a6545e8        debian:latest       "/bin/bash"         9 minutes ago       Exited (0) 8 minutes ago                       stoic_archimedes    

```

The ``commit`` command will commit your hanges and create a new untagged image:

```
$ docker commit 43270a6545e8
9cfa3ba0eb6d1ff63cebc20ee3f416d1ba98f399d717b47d762ecff1ba1808d6
$ docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             VIRTUAL SIZE
<none>              <none>              9cfa3ba0eb6d        5 seconds ago       94.8 MB
```

Untagged images can be run using their IMAGE ID:

```
$ docker run 9cfa3ba0eb6d samtools
```

You can list untagged images only:

```
$ docker images -f "dangling=true" -q
# a convenient command to remove untagged image
$ docker rmi $(docker images -f "dangling=true" -q)
```

Create a tagged image:

```
$ docker commit 43270a6545e8 interactive/samtools
786acd6cdd9911385a29a78913bc2d191efab1b833bf01d7994941ce64f38256
vagrant@vagrant-ubuntu-trusty-64:~/test-fd$ docker images
REPOSITORY             TAG                 IMAGE ID            CREATED             VIRTUAL SIZE
interactive/samtools   latest              786acd6cdd99        5 seconds ago       94.8 MB
```

### Use a Dockerfile

- [Simple example](Dockerfile)
- [Dockerfile for grape/mapping-gem](https://github.com/grape-pipeline/docker/blob/master/mapping/gem/Dockerfile)

#### Build

To create an untagged image just run:

```
$ mkdir test-build && cd test-build
$ wget https://raw.githubusercontent.com/emi80/docker-201502/master/tutorial/Dockerfile
$ docker build .
$ docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             VIRTUAL SIZE
<none>              <none>              5b401b00c9ac        38 seconds ago      86.44 MB
```

Create a tagged image:

```
$ docker build -t samtools . # also: ... -t myrepo/samtools:0.1.18 ...
```

