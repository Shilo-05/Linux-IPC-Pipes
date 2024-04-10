# Linux-IPC--Pipes
### Linux-IPC-Pipes


# Ex03-Linux IPC - Pipes

## AIM:
To write a C program that illustrate communication between two process using unnamed and named pipes

## DESIGN STEPS:

#### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

#### Step 2:

Write the C Program using Linux Process API - pipe(), fifo()

#### Step 3:

Testing the C Program for the desired output. 

## PROGRAM:

### C Program that illustrate communication between two process using unnamed pipes using Linux API system calls

```
$ cat pipe1.c 
#include<stdio.h>
#include<stdlib.h>
#include<sys/types.h> 
#include<sys/stat.h> 
#include<string.h> 
#include<fcntl.h> 
#include<unistd.h>
#include<sys/wait.h>
void server(int,int); 
void client(int,int); 
int main() 
{ 
int p1[2],p2[2],pid, *waits; 
pipe(p1); 
pipe(p2); 
pid=fork(); 
if(pid==0) { 
close(p1[1]); 
close(p2[0]); 
server(p1[0],p2[1]); return 0;
 } 
close(p1[0]); 
close(p2[1]); 
client(p1[1],p2[0]); 
wait(waits); 
return 0; 
} 


```

```

```

### OUTPUT:
```
$ ./pipe1.o 
cat> hello.txt
Hello world
to check pipe
```
```
$ ./pipe1.o 
ENTER THE FILE NAME :hello.txt	
CLIENT SENDING THE REQUEST .... PLEASE WAIT
THE RESULTS OF CLIENTS ARE ...... 
Hello world
to check pipe
```



  


### C Program that illustrate communication between two process using named pipes using Linux API system calls
```
#include <unistd.h>
#include <stdlib.h>
#include <stdio.h>
#include <sys/types.h>
#include <sys/stat.h>
int main()
{
int res = mkfifo("/tmp/my_fifo", 0777);
if (res == 0) printf("FIFO created\n");
exit(EXIT_SUCCESS);
}

```



'''


### OUTPUT:
```

$ ./fifo1.o 
FIFO created

$ ls -l /tmp/my_fifo 
prwxr-xr-x 1 gganesh gganesh 0 Sep 17 09:25 /tmp/my_fifo


```


# RESULT:
The program is executed successfully.
