```c
#include "common.h"

#include "my_thread.h"

extern pthread_mutex_t mutex_lock;

  

void *thread_func(void* arg){

    struct ClientThread *client_thread = (struct ClientThread *)arg;

    http_handler(client_thread->socket);

    close(client_thread->socket);

    pthread_mutex_lock(&mutex_lock);

    client_thread->is_running = false;

    pthread_mutex_unlock(&mutex_lock);

    printf("[INFO] Thread %ld finished.\n", client_thread->id);

    return NULL;

}
```
> 각 스레드 마다 일어나는 일인데 
> http_handler 함수로 처리를 하고 
> 소켓을 닫아 클라이언트와의 연결을 끊고
> 종료합니다.

