## What is docker? 
<!-- .element:  class="blue" style="margin-bottom: 1em;"-->

<div class="panel panel-default"> 
Docker is an open platform for developing, shipping, and running applications that allows to 
separate applications from the infrastructure
</div>

<!-- .element:  style="margin-top: 2em;"-->
[Docker userguide](https://docs.docker.com/userguide/) 


## The Docker Engine
<!-- .element:  class="blue" style="margin-bottom: 1em;"-->

lightweight and powerful open source container virtualization technology 

<h2><i class="fa fa-plus-circle"></i></h2>

set of tools and workflows for building and containerizing applications
<!-- .element: style="margin-bottom: 0.5em;"-->


## Containers
<!-- .element:  class="blue" style="margin-bottom: 1em;"-->

Docker uses: https://github.com/docker/libcontainer 

<div class="panel panel-default" style="margin-top: 2em;">
A container is a self contained execution environment that shares the kernel of the host system 
and which is (optionally) isolated from other containers in the system.
</div>


## Comparison to VMs
<!-- .element:  class="blue" style="margin-bottom: 1em;"-->

<div class="table-responsive">
<table class="table">
<tr>
  <td><p class="text-center">VM</p></td><td><p class="text-center">Docker container</p></td>
</tr>
<tr>
  <td><p class="text-center"><img src="https://s3.amazonaws.com/media-p.slid.es/uploads/ryanwalls/images/661990/Screen_Shot_2014-09-24_at_8.49.25_PM.png"/></p></td>
  <td><p class="text-center"><img src="https://s3.amazonaws.com/media-p.slid.es/uploads/ryanwalls/images/661977/Screen_Shot_2014-09-24_at_8.25.24_PM.png"/></p></td>
</tr>
<tr>
  <td><p class="text-center">Large<br>Consume significant CPU and memory<br>Not easily portable between VM environments<br>Hardware centric</p></td>
  <td><p class="text-center">Small<br>Basically zero memory and CPU overhead<br>Run in any linux environment<br>Application centric</p></td>
</tr>
</table>
</div>


## Why Docker?
<!-- .element: class="blue" style="margin-bottom: 1em;"-->

- separation of concerns - development vs deployment <!-- .element: style="margin-bottom: 0.6em;" -->
- rapid iteration of applications - fast container building and enhanced visibility of changes <!-- .element: style="margin-bottom: 0.6em;" -->
- low level virtualization - containers are fast and lightweigth <!-- .element: style="margin-bottom: 0.6em;" -->


## Inside Docker
<!-- .element: class="blue" style="margin-bottom: 1em;"-->

- Images
- Registries
- Containers


## Docker Images
<!-- .element: class="blue" style="margin-bottom: 1em;"-->

Images are read-only templates used to create Docker containers

<div class="panel panel-default" style="margin-top: 2em;">
It is easy to build new images or update existing images, or you can download Docker 
images that other people have already created
</div>

<!-- .element: style="margin-top: 2em;"-->
<i class="fa fa-arrow-right"></i> Docker images are the **build** component of Docker


## Docker registries
<!-- .element: class="blue" style="margin-bottom: 1em;"-->

<!-- .element: style="margin-bottom: 1.5em;"-->  
Docker registries are public or private stores from which you upload or download images. 

<div class="table-responsive">
<table class="table">
<tr>
<td>public Docker registry</td><td><i class="fa fa-arrow-right"></i> Docker Hub</td>
</tr>
<tr>
<td>CRG private registry</td><td><i class="fa fa-arrow-right"></i> docker-registry.linux.crg.es</td>
</tr>
</table>
</div>

<!-- .element: style="margin-top: 1em;"-->  
<i class="fa fa-arrow-right"></i> Docker registries are the **distribution** component of Docker.


## Docker containers
<!-- .element: class="blue" style="margin-bottom: 1em;"-->

<!-- .element: style="margin-bottom: 1.5em;"-->
Docker containers hold everything that is needed for an application to run. Each container is created from 
a Docker image and represents an isolated and secure application platform. 

<div class="panel panel-default" style="margin-top: 2em;">
Docker containers can be <span class="green">**run**</span>, <span class="green">**started**</span>, 
<span class="green">**stopped**</span>, <span class="green">**moved**</span>, and <span class="green">**deleted**<span>.
</div>

<!-- .element: style="margin-top: 2em;"-->
<i class="fa fa-arrow-right"></i> Docker containers are the **run** component of Docker.


## So what can you do?
<!-- .element: class="blue" style="margin-bottom: 1em;"-->

1. You can build Docker images that hold your applications.
2. You can create Docker containers from those Docker images to run your applications.
3. You can share those Docker images via Docker Hub or your own registry.


## Docker in bioinformatics
<!-- .element: class="blue" style="margin-bottom: 1em;"-->

- http://www.nucleotid.es - an assembler catalogue  <!-- .element: style="margin-bottom: 0.6em;" -->
- <span class="blue">**GRAPE**</span> - an automated RNAseq pipeline workflow using Nextflow and Docker  <!-- .element: style="margin-bottom: 0.6em;" -->


# Thanks!
