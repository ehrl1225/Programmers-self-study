```c
#include "common.h"

#include "my_thread.h"

  

#define THREAD_COUNT 10

pthread_mutex_t mutex_lock = PTHREAD_MUTEX_INITIALIZER;

  

int main(int argc, char **argv){

    int port, pid;

    Socket lsock, asock;

    pthread_mutex_init(&mutex_lock, NULL);

  

    struct sockaddr_in remote_sin;

    socklen_t remote_sin_len;

    pthread_t thread;

  

    if (argc < 2){

        printf("Usage: \n");

        printf("\t%s {port}: runs mini HTTP server. \n", argv[0]);

        exit(0);

    }

  

    port = atoi(argv[1]);

    printf("[INFO] The server will listen to port : %d.\n", port);

  

    lsock = socket(AF_INET, SOCK_STREAM, 0);

    if (lsock == SOCKET_ERROR){

        perror("[ERR] failed to create listen socket.\n");

        exit(1);

    }

  

    int optval = 1;

    if (setsockopt(lsock, SOL_SOCKET, SO_REUSEADDR, &optval, sizeof(optval)) < 0) {

        perror("[ERR] failed to set socket options.\n");

        exit(1);

    }

  

    if (bind_lsock(lsock, port) == SOCKET_ERROR){

        perror("[ERR] failed to bind listen socket.\n");

        exit(1);

    }

  

    if (listen(lsock, 10) == SOCKET_ERROR){

        perror("[ERR] failed to listen listen socket.\n");

        exit(1);

    }

  

    struct ClientThread *clientThreads = malloc(sizeof(struct ClientThread) * THREAD_COUNT);

    int thread_index = 0;

    while (1){

        printf("[INFO] waiting...\n");

        asock = accept(lsock, (struct sockaddr *)&remote_sin, &remote_sin_len);

        if (asock == SOCKET_ERROR){

            perror("[ERR] failed to accept.\n");

            continue;

        }

        bool found = false;

        pthread_mutex_lock(&mutex_lock);

        for (int i = 1; i <= THREAD_COUNT; i++){

            int real_index = (thread_index + i ) % THREAD_COUNT;

            if (clientThreads[real_index].is_running == false){

                clientThreads[i].socket = asock;

                clientThreads[i].is_running = true;

                found = true;

                thread_index = real_index;

                break;

            }

        }

        if (!found){

            printf("[ERR] No available thread.\n");

            close(asock);

            continue;

        }

        clientThreads[thread_index].socket = asock;

        clientThreads[thread_index].is_running = true;

        pthread_create(&thread, NULL, (void*)thread_func, (void *)(&clientThreads[thread_index]));

        clientThreads[thread_index].id = thread;

        pthread_mutex_unlock(&mutex_lock);

    }

  

    for (int thread_num = 0; thread_num < THREAD_COUNT; thread_num++){

        if (clientThreads[thread_num].is_running){

            pthread_join(clientThreads[thread_num].id, NULL);

            clientThreads[thread_num].is_running = false;

            printf("[INFO] Thread %d finished.\n", thread_num);

        }

    }

    close(lsock);

    free(clientThreads);

    pthread_mutex_destroy(&mutex_lock);

    return 0;

}
```
> 소켓을 만들고
> 소켓에 사용하려는 포트가 이미 열려 있어도 그 포트로 열라고 설정하고
> (이거는 실행할 때 편하게 하려고 한겁니다. 
> 다시 실행시킬 때 포트가 열려있다며 서버가 열리지 않는 문제를 해결합니다.)
> bind, listen을 통해 클라이언트를 받을 준비를 하고
> accept를 통해 클라이언트를 받습니다.
> 여기서는 클라이언트를 사용 가능한 스레드에 할당하고 스레드를 실행시키는 방법입니다.








