# Linux-Process-API-fork-wait-exec-
Ex02-Linux Process API-fork(), wait(), exec()
# Ex02-OS-Linux-Process API - fork(), wait(), exec()
Operating systems Lab exercise


# AIM:
To write C Program that uses Linux Process API - fork(), wait(), exec()

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux Process API - fork(), wait(), exec()

### Step 3:

Test the C Program for the desired output. 

# PROGRAM:

## C Program to print process ID and parent Process ID using Linux API system calls
```c

#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>
int main(void)
{	//variable to store calling function's process id
	pid_t process_id;
	//variable to store parent function's process id
	pid_t p_process_id;
	//getpid() - will return process id of calling function
	process_id = getpid();
	//getppid() - will return process id of parent function
	p_process_id = getppid();
	//printing the process ids

//printing the process ids
	printf("The process id: %d\n",process_id);
	printf("The process id of parent function: %d\n",p_process_id);
	return 0; }
```














## OUTPUT



![image-1](https://github.com/user-attachments/assets/09eb4cf1-d185-4980-8fae-e793b980d105)











## C Program to create new process using Linux API system calls fork() and exit()
```c
#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>
#include<stdlib.h>
int main()
{ int pid; 
pid=fork(); 
if(pid == 0) 
{ printf("Iam child my pid is %d\n",getpid()); 
printf("My parent pid is:%d\n",getppid()); 
exit(0); } 
else{ 
printf("I am parent, my pid is %d\n",getpid()); 
sleep(100); 
exit(0);} 
}


```










## OUTPUT
![image](https://github.com/user-attachments/assets/ded36029-7e1a-4fc7-8bcf-d6db475ce87a)



## C Program to execute Linux system commands using Linux API system calls exec() family
```c

#include <stdio.h>
#include <unistd.h>
#include <stdlib.h>
#include <sys/wait.h>
#include <sys/types.h>
int main()
{       int status;
        printf("Running ps with execlp\n");
        execl("ps", "ps", "ax", NULL);
        wait(&status);
        if (WIFEXITED(status))
                printf("child exited with status of %d\n", WEXITSTATUS(status));
        else
                puts("child did not exit successfully\n");
        printf("Done.\n");
printf("Running ps with execlp. Now with path specified\n");
        execl("/bin/ps", "ps", "ax", NULL);
        wait(&status);
        if (WIFEXITED(status))
                printf("child exited with status of %d\n", WEXITSTATUS(status));
        else
                puts("child did not exit successfully\n");
        printf("Done.\n");
        exit(0);}
```





















## OUTPUT![Screenshot from 2024-03-11 18-21-18](https://github.com/user-attachments/assets/5ba348b1-d17d-490c-a899-ec923e2f56d3)





![Screenshot from 2024-03-11 18-21-12](https://github.com/user-attachments/assets/44ef15c8-8464-49e9-b782-60d4f499512a)


![Screenshot from 2024-03-11 18-21-18](https://github.com/user-attachments/assets/8f8b95fa-a899-4b2b-8604-65f746cfeae5)

![Screenshot from 2024-03-11 18-21-24](https://github.com/user-attachments/assets/fe6b697a-11ef-4133-8ab9-ba2a431ffcb0)






# RESULT:
The programs are executed successfully.
