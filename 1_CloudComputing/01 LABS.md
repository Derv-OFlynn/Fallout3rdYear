### <mark style="background: #BABD00;">LAB 1 - 18/09/2024</mark>

#CloudComputing 

Docker, Python, Java, Vim and Go preinstalled

``console.cloud.google.com``

5GB free persistent storage space with a free gmail account

Can run Docker container from the cmd

``df -h`` is the command to see how much storage space you have left. `df`means "disk free" and the `-h` flag means to display it in a human readable format

The "home" partition is the only one with persistent storage

``builtin help`` is the Google Cloud Shell help command

You can use the Google Cloud Shell for 50 hours/week

"Boost mode" gives a performance boost for a few minutes

``ls -l`` is used to show file permissions


```sh
chmod [OPTIONS] MODE FILE...
```
![](https://i.imgur.com/CLKYpkh.png)
![](https://i.imgur.com/emLjMaA.png)
![](https://i.imgur.com/W5XjLu1.png)

The `wc` command allows you to count the number of lines, words, characters, and bytes of each given file or standard input and print the result. `wc` stands for word count.

![](https://i.imgur.com/3XPN9CD.png)

<mark style="background: #BABD00;">Lab exercise:</mark>

OPCODE
1. Allow the owner read access to the file and deny everyone else access to the file.
```Shell
chmod u=r,go=-rwx text.txt
```
2. Allows the owner and world to read the file but deny all access to the group.
    ```Shell
chmod u=r,go=-rwx text.txt
```
3. Deny access to the file for the owner, group and world.
```Shell
chmod ugo=-rwx text.txt
```
4. Grant the owner read and write access and grant the group and world read only access.
```Shell
chmod u=rw,og=r text.txt
```

OCTAL
1. Allow the owner read access to the file and deny everyone else access to the file.
```Shell
chmod 400 text.txt
```
2. Allows the owner and world to read the file but deny all access to the group.
```Shell
chmod 404 text.txt
```
3. Deny access to the file for the owner, group and world.
```Shell
chmod 000 text.txt
```
4. Grant the owner read and write access and grant the group and world read only access.
```Shell
chmod 644 text.txt
```

FILES

Create a file called `capital.txt` with the following five lines:

```
Dublin is the capital city of Ireland.
Ireland is viewed as the best country in the world by many people.
Dublin has a population greater than 1 million people.
There are many places to see and visit in Dublin.
The largest university in Ireland is TU Dublin.
```

Then, create a second file called `cities.txt` with the following contents:

```
Dublin
Cork
Belfast
Galway
Waterford
Kilkenny
```

1. Display the contents of the file `capital.txt`.
```Shell
cat capital.txt
```
2. Copy the contents of the files `capital.txt` and `cities.txt` into a new file `join.txt`. _Hint: Use the `cat` command and redirection._
```Shell
cat capital.txt cities.txt > join.txt
```
3. Display the count of the number of lines in the file `capital.txt`. _Hint: Use the `wc` command and piping or redirection._
```Shell
wc -l capital.txt
```
4. Display the count of the number of words in the file `capital.txt`
```Shell
wc -w capital.txt
```
5. Count and display just the number of bytes in the file `capital.txt`.
```Shell
wc -c capital.txt
```
6. Display a listing of the folders (and only the folders) in your home folder. _Hint: Use the `ls` and `grep` commands and piping._
```Shell
cd ..
ls -d */
```
7. Display a listing of the files (and only the files including hidden files) in your home folder.
```Shell
ls -a
```
8. Display the cities in the `cites.txt` file in sorted order.
```Shell
sort cities.txt
```
9. Create a new file called `sortedcites.txt` that contains the cities in `cites.txt` in sorted order. Hint: _Use the `sort` command and redirection_.
```Shell
sort cities.txt > sortedcities.txt
```
10. Display just the last two lines in the file `capital.txt`. Hint: _Use the `tail` command_.
```Shell
tail -n 2 capital.txt
```
11. Display just the first three lines in the file `capital.txt`. Hint: _Use the `head` command_.
```Shell
head -n 3 capital.txt
```
12. Display just the lines in the file `capital.txt` that contain the word `Dublin`. Hint: _Use the `grep` command_.
```Shell
grep Dublin capital.txt
```
13. Display just the lines in the file `capital.txt` that contain the word `dublin` case-insensitive.
```Shell
grep -i Dublin capital.txt
```
14. Display just the lines in the file `capital.txt` that **do not** contain the word `dublin` case-insensitive.
```Shell
grep -vi Dublin capital.txt
```
15. Display just the count of the lines in the file `capital.txt` that **do not** contain the word `dublin` case-insensitive.
```Shell
grep -vic Dublin capital.txt
```
16. Display just the line number(s) in the file `cities.txt` that contains the word `cork` case-insensitive.
```Shell
grep -n Cork cities.txt
```
17. Display just the first character of each line in the file `cities.txt`. Hint: _Use the `cat` and `cut` commands with piping_.
```Shell
cut -c 1 cities.txt
```
18. Display just the second last line of the file `capital.txt`. Hint: _Use the `cat`, `tail` and `head` commands with piping_.
```Shell
tail -n 2 capital.txt | head -n 1
```
19. Display the output of the command `ps -aux` _both_ to the screen _and_ redirect the stdout to the file `processes.txt`.
```Shell
ps -aux >> processes.txt | cat processes.txt
```
20. The command `seq` generates a sequence of numbers. For example, the command `seq 5` generates a sequence of numbers from 1 to 5. Try it out for yourself.
    
    1. Create a new file called `numbers.txt` with the sequence of numbers from 1 to 4 each on a separate line. Hint: _Use the `seq` command with redirection_.
    ```Bash
seq 4 > numbers.txt
```
    2. Now, using one command, appended the sequence numbers from 1 to 6 to the end of the file `numbers.txt`, each number on a separate line.
	```Shell
seq 6 >> numbers.txt
```
    3. Display the contents of the file `numbers.txt` sorted in ascending order.
	```Shell
sort numbers.txt
```
    4. Display the contents of the file `numbers.txt` sorted in ascending order, with duplicates removed. Hint: _Use the `cat`, `sort` and `uniq` commands with piping_.
	```Shell
sort numbers.txt | uniq
```
    1. Display how many times each line is duplicated in the file `numbers.txt`.
	```Shell
sort numbers.txt | uniq -c
```
    1. Display only the unique (non-duplicate lines) in the file. `numbers.txt`.
	```Shell
sort numbers.txt | uniq -u
```

PROCESSES

1. Start five processes in the background as indicated below:
    
    ```
    $ sleep 1000 &                              P1
    $ sleep 2000 &                              P2
    $ sleep 3000 &                              P3
    $ sleep 4000 &                              P4
    $ sleep 5000 &                              P5
    ```
    

- Please complete the following exercises, and write the commands and/or keystrokes you used as your answer.
- Terminate process P1 without using the `kill` command.
```Shell
^C
```
- Identify the process identifier (PID) of process P2.
```Shell
[2] 1575
```
- Terminate process P2 using the `kill` command.
```Shell
kill 1575
```
- Suspend process P3.
```Shell
kill -STOP 1576
```
- Bring process P4 to the foreground and then terminate it.
```Shell
fg %4
^C
```
- Terminate process P5 by force using the `kill` command.
```Shell
kill -9 1578
```
- Terminate process P3 without using the `kill` command.
```Shell
top
k
1576
```


# <mark style="background: #BABD00;">Lab 5 - Docker:</mark>

[Source](https://training.play-with-docker.com/ops-s1-hello/)

If you are familiar with VMs, you may be thinking this is pretty much just like running a virtual machine, except with a central repository of VM images. And in this simple example, that is basically true. But as you go through these exercises you will start to see important ways that Docker and containers differ from VMs. For now, the simple explanation is this:

- The VM is a _hardware_ abstraction: it takes physical CPUs and RAM from a host, and divides and shares it across several smaller virtual machines. There is an OS and application running inside the VM, but the virtualization software usually has no real knowledge of that.
- A container is an _application_ abstraction: the focus is really on the OS and the application, and not so much the hardware abstraction. Many customers actually use both VMs and containers today in their environments and, in fact, may run containers inside of VMs.

First command:
`docker container run hello-world`

![](https://i.imgur.com/Wh35rNn.png)

When you call `run`, the Docker client finds the image (alpine in this case), creates the container and then runs a command in that container. When you run `docker container run alpine`, you provided a command (`ls -l`), so Docker executed this command inside the container for which you saw the directory listing. After the `ls` command finished, the container shut down.

![](https://i.imgur.com/7lz3DOC.png)

Imagine booting up a virtual machine (VM), running a command and then killing it; it would take a minute or two just to boot the VM before running the command. A VM has to emulate a full hardware stack, boot an operating system, and then launch your app - it’s a virtualized _hardware_ environment. Docker containers function at the application layer so they skip most of the steps VMs require and just run what is required for the app. Now you know why they say containers are fast!

To run an interactive terminal use the `-it` command
```.term1
docker container run -it alpine /bin/sh
```

![](https://i.imgur.com/Tzr0YmR.png)

### <mark style="background: #BABD00;">Container Isolation:</mark>

<mark style="background: #BABD00;">Container Isolation</mark> is a critical security concept in the world of Docker containers! Even though each `docker container run` command used the same alpine **_image_**, each execution was a separate, isolated **_container_**. Each container has a separate filesystem and runs in a different namespace; by default a container has no way of interacting with other containers, even those from the same image.

![](https://i.imgur.com/RxSTJma.png)

![](https://i.imgur.com/0H7GLnp.png)

### <mark style="background: #BABD00;">Docker Terminology:</mark>

<mark style="background: #BABD00;">Images:</mark> The file system and configuration of our application which are used to create containers. To find out more about a Docker image, run `docker image inspect alpine`. In the demo above, you used the `docker image pull` command to download the **alpine** image. When you executed the command `docker container run hello-world`, it also did a `docker image pull` behind the scenes to download the **hello-world** image.

<mark style="background: #BABD00;">Containers:</mark> Running instances of Docker images — containers run the actual applications. A container includes an application and all of its dependencies. It shares the kernel with other containers, and runs as an isolated process in user space on the host OS. You created a container using `docker run` which you did using the alpine image that you downloaded. A list of running containers can be seen using the `docker container ls` command.

<mark style="background: #BABD00;">Docker daemon:</mark> The background service running on the host that manages building, running and distributing Docker containers.

<mark style="background: #BABD00;">Docker client:</mark> The command line tool that allows the user to interact with the Docker daemon.

<mark style="background: #BABD00;">Docker Hub:</mark> Store is, among other things, a [registry](https://store.docker.com/) of Docker images. You can think of the registry as a directory of all available Docker images. You’ll be using this later in this tutorial.

![](https://i.imgur.com/mzTsrhq.png)

### <mark style="background: #BABD00;">Image creation using a Dockerfile</mark>

Instead of creating a static binary image, we can use a file called a ``Dockerfile`` to create an image. The final result is essentially the same, but with a ``Dockerfile`` we are supplying the instructions for building the image, rather than just the raw binary files. This is useful because it becomes much easier to manage changes, especially as your images get bigger and more complex.

For example, if a new version of figlet is released we would either have to re-create our image from scratch, or run our image and upgrade the installed version of figlet. In contrast, a ``Dockerfile`` would include the `apt-get` commands we used to install figlet so that we - or anybody using the ``Dockerfile`` - could simply recompose the image using those instructions.

It is kind of like the old adage:

> _Give a sysadmin an image and their app will be up-to-date for a day, give a sysadmin a ``Dockerfile`` and their app will always be up-to-date_.

Ok, maybe that’s a bit of a stretch but ``Dockerfiles`` are powerful because they allow us to manage _how_ an image is built, rather than just managing binaries. In practice, ``Dockerfiles`` can be managed the same way you might manage source code: they are simply text files so almost any version control system can be used to manage ``Dockerfiles`` over time.

D