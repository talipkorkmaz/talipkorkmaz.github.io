---
layout: post
title: "How to install and run docker commands on windows"
comments: true
description: "This post is intented to show how to install and start docker instances on windows os.."
keywords: "docker install windows, docker, docker start, docker hello world, docker images, docker containers, hello, world, hello world"
---

#### Docker tutorial

I will not tell why docker should be used and why do anyone need this infrastructure tool.
It should be another blog post to tell in detail.

Firstly I used docker-tools installation for Windows 10 Enterprise and 64Bit operating system.

You can download docker-toolbox [here](https://www.docker.com/products/docker-toolbox)

Docker uses virtualization technology for creating docker machines and images.
So enable virtualization in your windows.Execute the command below.
```shell
bcdedit /set hypervisorlaunchtype auto
```
restart your compıuter.

After installing docker-tools, you can use the shortcut represented for you by docker.
Execute Docker Quickstart Terminal
If you take any error for not finding bash.exe error.Please correct the git bash.exe location in shourtcut (.lnk) file property

Firstly run the commands below and check the results.

```shell
docker info
docker-machine ls
docker ps
```

So lets start with an hello world as usual.
For this we will use the busybox image.

So lets pull the image firstly.

```shell
$ docker pull busybox
time="2017-04-09T15:38:47+03:00" level=info msg="Unable to use system certificate pool: crypto/x509: system root pool is not available on Windows"
Using default tag: latest
latest: Pulling from library/busybox
7520415ce762: Pull complete
Digest: sha256:32f093055929dbc23dec4d03e09dfe971f5973a9ca5cf059cbfb644c206aa83f
Status: Downloaded newer image for busybox:latest
```

Now lets list all images we pulled in a way.

```shell
$ docker images
time="2017-04-09T15:39:21+03:00" level=info msg="Unable to use system certificate pool: crypto/x509: system root pool is not available on Windows"
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
postgres            latest              ff0943ecbb3c        41 hours ago        267 MB
busybox             latest              00f017a8c2a6        4 weeks ago         1.11 MB
hello-world         latest              48b5124b2768        2 months ago        1.84 kB
```

So lets run our fresh installed docker image busybox.
```shell
docker run busybox
```
And the result is nothing.Because docker just found image,loads up the container ve run the command in container.
Since we gave no command to execute, docker exited.
So lets try with a simple echo message

```shell
docker run busybox echo "Hello from Ankara"
```
Now we see the result "Hello from Ankara" in our console.

By the way the warning message "crypto/x509: system root pool is not available on Windows" is a non-critical warning.
[It will be fixed in 17.04.](https://github.com/docker/docker/issues/30450)
You can check your version of docker with the command below.

```shell
$ docker version
time="2017-04-09T15:44:57+03:00" level=info msg="Unable to use system certificate pool: crypto/x509: system root pool is not available on Windows"
Client:
 Version:      17.03.1-ce
 API version:  1.27
 Go version:   go1.7.5
 Git commit:   c6d412e
 Built:        Tue Mar 28 00:40:02 2017
 OS/Arch:      windows/amd64

Server:
 Version:      17.04.0-ce
 API version:  1.28 (minimum version 1.12)
 Go version:   go1.7.5
 Git commit:   4845c56
 Built:        Wed Apr  5 18:45:47 2017
 OS/Arch:      linux/amd64
 Experimental: false
```

After executing the echo message with docker busybox image in any time we can list all the processes of docker

```shell
$ docker ps
time="2017-04-09T15:48:28+03:00" level=info msg="Unable to use system certificate pool: crypto/x509: system root pool is not available on Windows"
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS                      PORTS               NAMES
```

Now you will see nothing in result.
So lets see what happened in few beminutes before.

```shell
$ docker ps -a
time="2017-04-09T15:48:28+03:00" level=info msg="Unable to use system certificate pool: crypto/x509: system root pool is not available on Windows"
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS                      PORTS               NAMES
62de1e9908c8        busybox             "echo 'Hello from ..."   5 minutes ago       Exited (0) 5 minutes ago                        agitated_galileo
6a3f808ebbfa        busybox             "echo 'hello from ..."   7 minutes ago       Exited (0) 7 minutes ago                        mystifying_curie
091128aa8ebe        busybox             "sh"                     8 minutes ago       Exited (0) 8 minutes ago                        priceless_mayer
```

What abaout running multiple commands in image?
Yes you need this to build your image with custom commands.
So the way is :

```shell
$ docker run -it busybox sh
time="2017-04-09T15:52:12+03:00" level=info msg="Unable to use system certificate pool: crypto/x509: system root pool is not available on Windows"
/ # ls
bin   dev   etc   home  proc  root  sys   tmp   usr   var
/ # cat /proc/meminfo
MemTotal:        1019656 kB
MemFree:          362424 kB
MemAvailable:     628812 kB
```

-it parameters are for attaching us to the container.

Now lets learn the deletion of containers.
As a rule of thumb, clean the images after you finish your job.
For deletion use the container id.

```shell
$ docker ps -a
time="2017-05-02T19:27:34+03:00" level=info msg="Unable to use system certificate pool: crypto/x509: system root pool is not available on Windows"
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS                      PORTS               NAMES
4c214278668a        busybox             "sh"                     6 minutes ago       Exited (0) 6 minutes ago                        naughty_heisenberg
2e2a6adf2ed4        busybox             "echo 'Hello from ..."   7 minutes ago       Exited (0) 7 minutes ago                        elated_agnesi
be6ffe24f734        hello-world         "/hello"                 12 minutes ago      Exited (0) 12 minutes ago                       hopeful_bhaskara
904e780185b5        busybox             "echo talikorkmaz"       3 weeks ago         Exited (0) 3 weeks ago                          nifty_mcclintock

talipk@TALIP-KORKMAZ MINGW64 ~
$ docker rm be6ffe24f734
time="2017-05-02T19:27:45+03:00" level=info msg="Unable to use system certificate pool: crypto/x509: system root pool is not available on Windows"
be6ffe24f734

talipk@TALIP-KORKMAZ MINGW64 ~
$ docker ps -a
time="2017-05-02T19:27:49+03:00" level=info msg="Unable to use system certificate pool: crypto/x509: system root pool is not available on Windows"
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS                     PORTS               NAMES
4c214278668a        busybox             "sh"                     7 minutes ago       Exited (0) 6 minutes ago                       naughty_heisenberg
2e2a6adf2ed4        busybox             "echo 'Hello from ..."   7 minutes ago       Exited (0) 7 minutes ago                       elated_agnesi
904e780185b5        busybox             "echo talikorkmaz"       3 weeks ago         Exited (0) 3 weeks ago                         nifty_mcclintock

```

But there are lots of images which I'm done.So lets delete all with a small script.

```shell
$ docker rm $(docker ps -a -q -f status=exited)
```
or
```shell
$ docker rmi $(docker images | awk '{print $3}')
```

I always use --rm parameter when executing an image.Because --rm is very useful in docker run command.It automatically deletes after the execution done.
Here is the example

```shell
$ docker run --rm busybox echo "hello from busybox"
time="2017-04-09T15:59:01+03:00" level=info msg="Unable to use system certificate pool: crypto/x509: system root pool is not available on Windows"
hello from busybox
```
```shell
$ docker ps -a
time="2017-04-09T15:59:03+03:00" level=info msg="Unable to use system certificate pool: crypto/x509: system root pool is not available on Windows"
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
```

Now lets clear what we used and what terminology is learnt with the commands above.

* **Docker Image** -> An image is a filesystem and parameters to use at runtime. It doesn’t have state and never changes. Docker container will load this.
* **Docker Container** -> A container is a running instance of an image.We create a container with docker run command.And docker ps will list running containers.
* **Docker Deamon** -> The host for managing building,running and distrubiting.Clients are talking with this host and host run in operating system.
* **Docker Client** -> The CLI tool that allows us to interact with docker deamon.Also Kitematic provides gui for this. https://kitematic.com/
* **Docker Hub** -> This hub is a registry for docker images.We can pull images from here and also we can search whatevery we want.

Example :

```shell
$ docker search "postgres"
time="2017-04-09T16:07:28+03:00" level=info msg="Unable to use system certificate pool: crypto/x509: system root pool is not available on Windows"
NAME                              DESCRIPTION                                     STARS     OFFICIAL   AUTOMATED
postgres                          The PostgreSQL object-relational database ...   3407      [OK]
kiasaki/alpine-postgres           PostgreSQL docker image based on Alpine Linux   30                   [OK]
abevoelker/postgres               Postgres 9.3 + WAL-E + PL/V8 and PL/Python...   10                   [OK]
macadmins/postgres                Postgres that accepts remote connections b...   8                    [OK]
```