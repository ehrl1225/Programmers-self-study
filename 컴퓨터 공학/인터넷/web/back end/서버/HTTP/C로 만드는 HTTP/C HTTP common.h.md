```c
#ifndef COMMON_H

#define COMMON_H

  

#define BUF_SIZE 1000

#define HEADER_FMT "HTTP/1.1 %d %s\nContent-Length: %ld\nContent-Type: %s\n\n"

#define NOT_FOUND_CONTENT   "<h1>404 Not Found</h1>\n"

#define SERVER_ERROR_CONTENT "<h1>500 Internal Server Error</h1>\n"

#define SOCKET_ERROR -1

  

#include <stdio.h>

#include <string.h>

#include <stdlib.h>

#include <unistd.h>

#include <fcntl.h>

#include <signal.h>

#include <sys/types.h>

#include <sys/stat.h>

#include <sys/socket.h>

#include <arpa/inet.h>

#include <pthread.h>

#include <stdbool.h>

  

typedef int Socket;

#endif // COMMON_H
```
소켓 값이 int이지만 구분을 위해 Socket이라고 작성했습니다.
리눅스 전용으로 만들어져 있어 windows에는 없는 라이브러리가 있습니다.
