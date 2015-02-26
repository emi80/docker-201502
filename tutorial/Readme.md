# Docker tutorial

In the following tutorial we are going to play around with some Docker comands. For the purpose, we use an Ubuntu virtual machine with Docker up and running and some already installed images.

## Course virtual machine

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

## Docker commands
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

Nice way to remove untagged images, i.e. images with no tag associated to them:

```
$ docker rmi $(docker images -f "dangling=true" -q)
```

## Create images interactively

```
$ docker run -t -i debian
root@43270a6545e8:/# apt -get update
root@43270a6545e8:/# apt -get install samtools
root@43270a6545e8:/# exit
$ docker commit 43270a6545e8
9cfa3ba0eb6d1ff63cebc20ee3f416d1ba98f399d717b47d762ecff1ba1808d6
$ docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             VIRTUAL SIZE
<none>              <none>              9cfa3ba0eb6d        5 seconds ago       94.8 MB
```

## Create images from a Dockerfile

Dockerfiles:
- [Simple example](Dockerfile)
- [Dockerfile for grape/mapping-gem](https://github.com/grape-pipeline/docker/blob/master/mapping/gem/Dockerfile)

#### Build

```
$ mkdir test-build && cd test-build
$ wget https://raw.githubusercontent.com/emi80/docker-201502/master/tutorial/Dockerfile
$ docker build .
```

The above command will create an untagged image:
```
$ docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             VIRTUAL SIZE
<none>              <none>              5b401b00c9ac        38 seconds ago      86.44 MB
$ docker run 5b401b00c9ac samtools
```

You can create a tag image:

```
$ docker build -t samtools . # also: ... -t myrepo/samtools:0.1.18 ...
$ docker run samtools samtools 
```

