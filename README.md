# Linux-IPC-Shared-memory
Ex06-Linux IPC-Shared-memory

# AIM:
To Write a C program that illustrates two processes communicating using shared memory.

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux Process API - Shared Memory

### Step 3:

Execute the C Program for the desired output. 

# PROGRAM:
```
DEVELOPED BY: VESLIN ANISH A REGISTER NUMBER:212223240175

## Write a C program that illustrates two processes communicating using shared memory.
#include <stdio.h>
#include <sys/ipc.h>
#include <sys/shm.h>

int main()
{
	// Generate a unique key using ftok
	key_t key = ftok("shmfile", 65);

	// Get an identifier for the shared memory segment using shmget
	int shmid = shmget(key, 1024, 0666 | IPC_CREAT);
      printf("Shared memory id = %d \n",shmid);
// Attach to the shared memory segment using shmat
	char* str = (char*)shmat(shmid, (void*)0, 0);
	
    printf("Write Data : ");
	fgets(str, 1024, stdin);

	printf("Data written in memory: %s\n", str);

	// Detach from the shared memory segment using shmdt
	shmdt(str);

	return 0;
}
```





## OUTPUT
![WhatsApp Image 2024-04-29 at 22 26 56_4dbc06f1](https://github.com/veslin23000303/Linux-IPC-Shared-memory/assets/151148539/04b255d4-b6e0-4769-a1e9-875277f78b33)


# RESULT:
The program is executed successfully.
