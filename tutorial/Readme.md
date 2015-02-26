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
The run command will create and start a container based on the specified image.

```
$ docker run grape/base
```
