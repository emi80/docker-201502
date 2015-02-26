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
Here is a series of some useful Docker commands. PLease check [Docker documentation](https://docs.docker.com/reference/commandline/cli/) for the complete list.

#### Check installed images

```
$ docker images
```

#### Search the Docker hub

```
$ docker search grape
```

#### Download images from the Docker hub

```
$ docker pull grape/base
```

#### Run a contatiner
The ``run`` command will create and start a container based on the specified image.

```
$ docker run grape/base env
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

The combination of ``-a`` and ``-q`` options is very usefull when you want to cleanup non-running containers:
```
$ docker rm $(docker ps -a -q)
```

Docker will conveniently fail to delete running containers and report the error while the stopped ones will be deleted.
