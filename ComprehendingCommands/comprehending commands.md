# COMPREHENDING COMMANDS

## Cat: not the pet, but the command!

cat - concatenate       
this command reads the file put as the argument. we can put multiple arguments too.


for this task all I had to do was put the command `cat` and argument `flag`, as given in the instructions. 


```````
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{QA2D907V6m9wr53XIjqPCEmpurN.dFzN1QDLwIzN0czW}
```````

## Catting Absolute Paths

given that the absolute path is `/flag`, this task becomes easy, as cat can also read absolute paths.

therefore, I entered `cat /flag` while in the home directory and got the flag.

`````
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{cn6ugyLbq3tyEmXXW2Qv3ZK2CxJ.dlTM5QDLwIzN0czW}

````````````



## More Catting Practice

on opening my terminal, the absolute path to be used was mentioned. it was `/opt/capstone/windows/flag`.        
so I used the cat command with this argument and got the flag.

```````
You cannot use the 'cd' command in this level, and must retrieve the flag by
absolute path. Plus, I hid the flag in a different directory! You can find it
in the file /opt/capstone/windows/flag. Go cat it out **without** cding into
that directory!
hacker@commands~more-catting-practice:~$ cat /opt/capstone/windows/flag
pwn.college{A6unAi8Yvt73k99K2Ib2tVZeNhZ.dBjM5QDLwIzN0czW}
`````````

## Grepping for a Needle in a Haystack

grep - global regular expression print

grep is used to filter out stuff from very huge files and give us only the parts of it we need. 
to get the flag from `/challenge/data.txt` I typed `grep pwn.college /challenge/data.txt` because this will display only the lines of code within the file that contain "pwn.college"
      
``````
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt
pwn.college{UlwxTNU-QIGRlIfODS6PhKsPR-p.ddTM4QDLwIzN0czW}
``````

## Listing Files

ls - lists files within the directory

to get the flag, first I listed all the files in `/challenge` directory.

```````
hacker@commands~listing-files:/$ cd /challenge
hacker@commands~listing-files:/challenge$ ls
17999-renamed-run-10370  DESCRIPTION.md
```````
at first i tried `cat DESCRIPTION.md` but that just gave me the task descprition present on the website.
so I realised that the flag was in `17999-renamed-run-10370`

I did face some problems with trying to open the file, first I tried to concatenate it but it gave me the following output: 

``````
hacker@commands~listing-files:/challenge$ cat 17999-renamed-run-10370
#!/opt/pwn.college/bash

echo "Yahaha, you found me! Here is your flag:"
cat /flag
``````

I understood that I was right about getting the file from `17999-renamed-run-10370` but I realised the `cat` cat was not right.
to figure out how to open this, I had to go back and read my .md file of the Pondering Paths module.

from the Explicit Paths task, I realised that I just needed to use `./17999-renamed-run-10370` to open it, since I was already inside the `/challenge` directory.
this would be equivalent to `/challenge/17999-renamed-run-10370`

```````
hacker@commands~listing-files:/challenge$ ./17999-renamed-run-10370
Yahaha, you found me! Here is your flag:
pwn.college{QmSimM6b4xoDJqux7nhMuSUqi_L.dhjM4QDLwIzN0czW}
````````

## Touching Files

touch command creates a new file.

to create the pwn and college files in the /tmp directory, first I changed directory to `/tmp`
`````
hacker@commands~touching-files:~$ cd /tmp
```````

then I used the `touch` command to create pwn and college.   
on listing the files in `/tmp` it shows the new files, which means file creation was successful.

```````
hacker@commands~touching-files:/tmp$ touch pwn
hacker@commands~touching-files:/tmp$ touch college
hacker@commands~touching-files:/tmp$ ls
bin  college  hsperfdata_root  pwn  tmp.XvrUsDZh8M
```````

therefore, as mentioned in the instructions, I ran `/challenge/run` to get the flag.


``````
hacker@commands~touching-files:/tmp$ /challenge/run
Success! Here is your flag:
pwn.college{4xwy4vrkZadop6pfCFBDgHDp-JI.dBzM4QDLwIzN0czW}
```````

## Removing Files

rm = remove file

to remove the delete_me file from `~` I used the `rm` command and then I ran `/challenge/check`

````
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{sjgb4v42__X8pg-hOj03Jy_iFDb.dZTOwUDLwIzN0czW}

`````


## Hidden Files

when we use the `ls` command, linux hides files that begin with .

in this case, we need to use `ls -a` to get such files.

first I used the normal `ls` command in the / directory.
````
hacker@commands~hidden-files:~$ cd /
hacker@commands~hidden-files:/$ ls
bin        dev   lib    libx32  nix   root  srv  usr
boot       etc   lib32  media   opt   run   sys  var
challenge  home  lib64  mnt     proc  sbin  tmp
`````

then I used the `ls -a` command:

`````
hacker@commands~hidden-files:/$ ls -a
.                      challenge  lib64   proc  tmp
..                     dev        libx32  root  usr
.dockerenv             etc        media   run   var
.flag-246642188516183  home       mnt     sbin
bin                    lib        nix     srv
boot                   lib32      opt     sys
`````

here I found the flag file. it is named `.flag-246642188516183`
      
then, all I had to do was execute it:

````
hacker@commands~hidden-files:/$ cat ./.flag-246642188516183
pwn.college{YdWy-mcB1zFAAPAH1UYqyspz1MV.dBTN4QDLwIzN0czW}
`````

## An Epic Filesystem Quest

CLUES:     
0. Your first clue is in /. Head on over there.
1. Look around with ls. There'll be a file named HINT or CLUE or something along those lines!
cat that file to read the clue!
2. Depending on what the clue says, head on over to the next directory (or don't!).
3. Follow the clues to the flag!

I followed clues 0 and 1 to get: 

`````
hacker@commands~an-epic-filesystem-quest:~$ cd /
hacker@commands~an-epic-filesystem-quest:/$ ls
LEAD       dev   lib     media  proc  srv  var
bin        etc   lib32   mnt    root  sys
boot       flag  lib64   nix    run   tmp
challenge  home  libx32  opt    sbin  usr
``````

the LEAD file caught my eye, so I opened it to find:

````
hacker@commands~an-epic-filesystem-quest:/$ cat LEAD
Tubular find!
The next clue is in: /usr/local/lib/python3.8/dist-packages/sympy/physics/hep

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
`````

since I couldn't use `cd`, I had to make my argument an absolute path:

````
hacker@commands~an-epic-filesystem-quest:/$ ls /usr/local/lib/python3.8/dist-packages/sympy/physics/hep
SNIPPET-TRAPPED  __pycache__        tests
__init__.py      gamma_matrices.py
`````
since the previous clue mentioned a trapped snippet, I opened the `SNIPPET-TRAPPED` file (without using cd again):

````
hacker@commands~an-epic-filesystem-quest:/$ cat /usr/local/lib/python3.8/dist-packages/sympy/physics/hep/SNIPPET-TRAPPED
Congratulations, you found the clue!
The next clue is in: /opt/ghidra/Ghidra/Features/FileFormats/data/languages

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
````

to find hidden files, we need to use `ls -a` and on doing so I got:

````
hacker@commands~an-epic-filesystem-quest:/$ ls -a /opt/ghidra/Ghidra/Features/FileFormats/data/languages
.   .TEASER         minidump.opinion
..  apport.opinion  pagedump.opinion
````

I assumed the `.TEASER` file would contain the next clue, so I opened it:

````
hacker@commands~an-epic-filesystem-quest:/$ cat /opt/ghidra/Ghidra/Features/FileFormats/data/languages/.TEASER
Congratulations, you found the clue!
The next clue is in: /usr/share/doc/mysql-server

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/$
````


I then listed the files in `/usr/share/doc/mysql-server` :

```
hacker@commands~an-epic-filesystem-quest:/$ ls /usr/share/doc/mysql-server
NUGGET  copyright
```

on trying to open `NUGGET` using the absolute path, I was not able to access it: 

```
hacker@commands~an-epic-filesystem-quest:/$ cat /usr/share/doc/mysql-server/NUGGET
cat: /usr/share/doc/mysql-server/NUGGET: Permission denied
```

I read the previous clue and realised my mistake. I needed to use the `cd` command to make it readable. so that's what I did:   
```
hacker@commands~an-epic-filesystem-quest:/$ cd /usr/share/doc/mysql-server
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/mysql-server$ cat NUGGET
Congratulations, you found the clue!
The next clue is in: /opt/busybox/busybox-1.33.2/include/config/feature/use/bss

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
```

I changed directories again to `/opt/busybox/busybox-1.33.2/include/config/feature/use/bss` and then listed its contents:
````
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/mysql-server$ cd /opt/busybox/busybox-1.33.2/include/config/feature/use/bss
hacker@commands~an-epic-filesystem-quest:/opt/busybox/busybox-1.33.2/include/config/feature/use/bss$ ls
README  tail.h
````

then I read the README file using `cat`

```
hacker@commands~an-epic-filesystem-quest:/opt/busybox/busybox-1.33.2/include/config/feature/use/bss$ cat README
Tubular find!
The next clue is in: /opt/angr-management/_internal/jedi/third_party/typeshed/third_party/2and3/cryptography/hazmat/primitives/twofactor

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
```

I used `cd` again to go to `opt/angr-management/_internal/jedi/third_party/typeshed/third_party/2and3/cryptography/hazmat/primitives/twofactor` and then used `ls -a` to see all the files in it, including hidden ones.


```
hacker@commands~an-epic-filesystem-quest:/opt/busybox/busybox-1.33.2/include/config/feature/use/bss$ cd  /opt/angr-management/_internal/jedi/third_party/typeshed/third_party/2and3/cryptography/hazmat/primitives/twofactor
hacker@commands~an-epic-filesystem-quest:/opt/angr-management/_internal/jedi/third_party/typeshed/third_party/2and3/cryptography/hazmat/primitives/twofactor$ ls -a
.  ..  .BRIEF  __init__.pyi  hotp.pyi  totp.pyi
hacker@commands~an-epic-filesystem-quest:/opt/angr-management/_internal/jedi/third_party/typeshed/third_party/2and3/cryptography/hazmat/primitives/twofactor$
```
I then concatenated the `.BRIEF` file.
````
hacker@commands~an-epic-filesystem-quest:/opt/angr-management/_internal/jedi/third_party/typeshed/third_party/2and3/cryptography/hazmat/primitives/twofactor$ cat .BRIEF
Tubular find!
The next clue is in: /usr/share/racket/pkgs/shell-completion/compiled
````

I used `cd` to go to the directory with the next clue and listed the contents:
```
hacker@commands~an-epic-filesystem-quest:/opt/angr-management/_internal/jedi/third_party/typeshed/third_party/2and3/cryptography/hazmat/primitives/twofactor$ cd /usr/share/racket/pkgs/shell-completion/compiled
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/shell-completion/compiled$ ls
EVIDENCE      info_rkt.zo            list-collects_rkt.zo
info_rkt.dep  list-collects_rkt.dep
```

then I read EVIDENCE:

```
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/shell-completion/compiled$ cat EVIDENCE
Tubular find!
The next clue is in: /opt/linux/linux-5.4/drivers/iio/humidity
```

Again I used `ls` and `cd` to find a fiel called REVELATION, which I opened using `cat`

```
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/shell-completion/compiled$ ls /opt/linux/linux-5.4/drivers/iio/humidity
Kconfig     hdc100x.c              hts221_i2c.c
Makefile    hid-sensor-humidity.c  hts221_spi.c
REVELATION  hts221.h               htu21.c
am2315.c    hts221_buffer.c        si7005.c
dht11.c     hts221_core.c          si7020.c
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/shell-completion/compiled$ cd /opt/linux/linux-5.4/drivers/iio/humidity
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/iio/humidity$ cat REVELATION
Great sleuthing!
The next clue is in: /opt/angr-management/_internal/pypcode/processors/8085

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
```

here I couldnt use `cd`, so I directly listed the contents by using the absolute path as my argument.
```
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/iio/humidity$ ls /opt/angr-management/_internal/pypcode/processors/8085
BLUEPRINT-TRAPPED  data

```

when I opened the `BLUEPRINT-TRAPPED` file, I finally got the reached the end of the quest.
```
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/iio/humidity$ cat /opt/angr-management/_internal/pypcode/processors/8085/BLUEPRINT-TRAPPED
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!
It is: pwn.college{ktPTKEQ8sY3vUw_mdGYaXsYxZpd.dljM4QDLwIzN0czW}
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/iio/humidity$

```


## Making Directories

mkdir = command to make directory

to make directory, first i changed the cwd to `/tmp`    
then I used `mkdir` to create directory `pwn` in the cwd
then I made a file called college using the `touch` command, after which I ran `/challenge/run` to get the flag
````
hacker@commands~making-directories:~$ cd /tmp
hacker@commands~making-directories:/tmp$ mkdir pwn
hacker@commands~making-directories:/tmp$ cd ./pwn
hacker@commands~making-directories:/tmp/pwn$ touch college
hacker@commands~making-directories:/tmp/pwn$ ls
college
hacker@commands~making-directories:/tmp/pwn$ /challenge/run
Success! Here is your flag:
pwn.college{oajCxbgQ-OXUEUjmh0rkrBiuMbG.dFzM4QDLwIzN0czW}
````

## Finding Files

find = command to find files.    
if search location isn't specified, it uses cwd.   
if search criteria isn't specified, it matches all files.      
to search by name, use `find -name insert_name `

first I listed everything present in /.
````
hacker@commands~finding-files:~$ cd /
hacker@commands~finding-files:/$ ls
bin        dev   lib    libx32  nix   root  srv  usr
boot       etc   lib32  media   opt   run   sys  var
challenge  home  lib64  mnt     proc  sbin  tmp
````
I then went to the /challenge directory:

````
hacker@commands~finding-files:/tmp$ cd /challenge
hacker@commands~finding-files:/challenge$ find flag
find: ‘flag’: No such file or directory
hacker@commands~finding-files:/challenge$ ls
DESCRIPTION.md  run
hacker@commands~finding-files:/challenge$ ./run
The flag is hidden (and readable) somewhere on the filesystem. Go find it!
````
I used the `find` command while specifying the location to be `/` and the criteria to be `-name`
````
hacker@commands~finding-files:/$ find / -name flag
find: ‘/root’: Permission denied
find: ‘/proc/1/task/1/fd’: Permission denied
find: ‘/proc/1/task/1/fdinfo’: Permission denied
find: ‘/proc/1/task/1/ns’: Permission denied
find: ‘/proc/1/fd’: Permission denied
find: ‘/proc/1/map_files’: Permission denied
find: ‘/proc/1/fdinfo’: Permission denied
find: ‘/proc/1/ns’: Permission denied
find: ‘/proc/7/task/7/fd’: Permission denied
find: ‘/proc/7/task/7/fdinfo’: Permission denied
find: ‘/proc/7/task/7/ns’: Permission denied
find: ‘/proc/7/fd’: Permission denied
find: ‘/proc/7/map_files’: Permission denied
find: ‘/proc/7/fdinfo’: Permission denied
find: ‘/proc/7/ns’: Permission denied
find: ‘/var/log/private’: Permission denied
find: ‘/var/log/apache2’: Permission denied
find: ‘/var/log/mysql’: Permission denied
find: ‘/var/cache/ldconfig’: Permission denied
find: ‘/var/cache/apt/archives/partial’: Permission denied
find: ‘/var/cache/private’: Permission denied
find: ‘/var/lib/apt/lists/partial’: Permission denied
find: ‘/var/lib/php/sessions’: Permission denied
find: ‘/var/lib/mysql-files’: Permission denied
find: ‘/var/lib/private’: Permission denied
find: ‘/var/lib/mysql-keyring’: Permission denied
find: ‘/var/lib/mysql’: Permission denied
find: ‘/tmp/tmp.XvrUsDZh8M’: Permission denied
find: ‘/run/mysqld’: Permission denied
find: ‘/run/sudo’: Permission denied
find: ‘/etc/ssl/private’: Permission denied
/usr/local/lib/python3.8/dist-packages/pwnlib/flag
/usr/local/share/radare2/5.9.5/flag
/opt/linux/linux-5.4/arch/mips/include/asm/mach-jz4740/flag
/opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/flag
/opt/radare2/libr/flag
/nix/store/pmvk2bk4p550w182rjfm529kfqddnvh3-python3.11-pwntools-4.12.0/lib/python3.11/site-packages/pwnlib/flag
/nix/store/1yagn5s8sf7kcs2hkccgf8d0wxlrv5sz-radare2-5.9.0/share/radare2/5.9.0/flag
````

from this long list, I had access to only 7 paths, so I used trial and error for each of them and eventually found the flag in `/opt/linux/linux-5.4/arch/mips/include/asm/mach-jz4740/flag`. 

trial 1:
````
hacker@commands~finding-files:~$ cat /usr/local/lib/python3.8/dist-packages/pwnlib/flag
cat: /usr/local/lib/python3.8/dist-packages/pwnlib/flag: Is a directory
hacker@commands~finding-files:~$ ls /usr/local/lib/python3.8/dist-packages/pwnlib/flag
__init__.py  __pycache__  flag.py
````
since the files are python files, I moved onto trial 2:
````
hacker@commands~finding-files:~$ cat /usr/local/share/radare2/5.9.5/flag
cat: /usr/local/share/radare2/5.9.5/flag: Is a directory
hacker@commands~finding-files:~$ ls /usr/local/share/radare2/5.9.5/flag
tags.r2
````
since this does not match the flag, I went to trial 3:
```
hacker@commands~finding-files:~$ cat /opt/linux/linux-5.4/arch/mips/include/asm/mach-jz4740/flag
pwn.college{YW0rP0FumONTa8FgVn2Dy5cEwtD.dJzM4QDLwIzN0czW}
````

## Linking Files
ln -s = command and argument to create soft link.

used https://youtu.be/4-vye3QFTFo?si=lzlYa6zYxpxzkf7B to learn about soft link and hard link on linux.    
learnt that symlinks contain the file name, which the system reads and then gets data from the file whose name is in it. symlinks are meaningless if the original file is deleted.    
on the other hand, hardlinks are alternate addresses to the same file contents, therefore deletion of original file will not affect the hardlink.      


to do this task, I tried to symlink `/flag` to `/home/hacker/not-the-flag` but this was not working and it showed the error:        
`ln: failed to create symbolic link '/home/hacker/not-the-flag': File exists`

so the only way was to remove `/home/hacker/not-the-flag` and then try the linking, which worked.


```
hacker@commands~linking-files:~$ rm /home/hacker/not-the-flag
hacker@commands~linking-files:~$ ln -s /flag /home/hacker/not-the-flag
hacker@commands~linking-files:~$ /challenge/catflag
About to read out the /home/hacker/not-the-flag file!
pwn.college{QQcEZ_winrmqArZ04SsVOF1epjC.dlTM1UDLwIzN0czW}
hacker@commands~linking-files:~$
```

