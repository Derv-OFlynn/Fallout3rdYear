### <mark style="background: #BABD00;">LAB 1 - 18/09/2024</mark>

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
    
- Identify the process identifier (PID) of process P2.
    
- Terminate process P2 using the `kill` command.
    
- Suspend process P3.
    
- Bring process P4 to the foreground and then terminate it.
    
- Terminate process P5 by force using the `kill` command.
    
- Terminate process P3 without using the `kill` command.