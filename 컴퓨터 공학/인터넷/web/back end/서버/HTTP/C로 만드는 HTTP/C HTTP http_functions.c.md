```c
#include "common.h"

#include "http_functions.h"

  

int bind_lsock(int lsock, int port){

    struct sockaddr_in sin;

    sin.sin_family = AF_INET;

    sin.sin_addr.s_addr = htonl(INADDR_ANY);

    sin.sin_port = htons(port);

    return bind(lsock, (struct sockaddr *)&sin, sizeof(sin));

}

  

void fill_header(char *header, int status, long len, char *type){

    char status_text[40];

    switch (status){

        case 200:

            strcpy(status_text, "OK");

            break;

        case 404:

            strcpy(status_text, "Not Found");

            break;

        case 500:

        default:

            strcpy(status_text, "Internal Server Error");

            break;

    }

    sprintf(header, HEADER_FMT, status, status_text, len, type);

}

  

void find_mime(char *ct_type, char *uri){

    char *ext = strrchr(uri, '.');

    if (!strcmp(ext, ".html"))

        strcpy(ct_type, "text/html");

    else if (!strcmp(ext, ".jpg") || !strcmp(ext, "jpeg"))

        strcpy(ct_type, "image/jpeg");

    else if (!strcmp(ext, ".png"))

        strcpy(ct_type, "image/png");

    else if (!strcmp(ext, ".css"))

        strcpy(ct_type, "text/css");

    else if (!strcmp(ext, ".js"))

        strcpy(ct_type, "text/javascript");

    else

        strcpy(ct_type, "text/plain");

}

  

void handle_404(int asock){

    char header[BUF_SIZE];

    fill_header(header, 404, sizeof(NOT_FOUND_CONTENT), "text/html");

  

    write(asock, header, strlen(header));

    write(asock, NOT_FOUND_CONTENT, sizeof(NOT_FOUND_CONTENT));

}

  

void handle_500(int asock){

    char header[BUF_SIZE];

    fill_header(header, 500, sizeof(SERVER_ERROR_CONTENT), "text/html");

  

    write(asock, header, strlen(header));

    write(asock, SERVER_ERROR_CONTENT, sizeof(SERVER_ERROR_CONTENT));

}

  

void http_handler(int asock){

    char header[BUF_SIZE];

    char buf[BUF_SIZE];

  

    if (read(asock, buf, BUF_SIZE) < 0){

        perror("[ERR] Failed to read request.\n");

        handle_500(asock);

        return;

    }

  

    char *method = strtok(buf, " ");

    char *uri = strtok(NULL, " ");

  

    if (method == NULL || uri == NULL){

        perror("[ERR] Failed to identify method, URI.\n");

        handle_500(asock);

        return;

    }

  

    printf("[INFO] Handling Request: method=%s, URI=-%s\n", method, uri);

  

    char safe_uri[BUF_SIZE];

    char *local_uri;

    struct stat st;

  

    strcpy(safe_uri, uri);

    if (!strcmp(safe_uri, "/"))

        strcpy(safe_uri, "/index.html");

    local_uri = safe_uri + 1;

    if (stat(local_uri, &st) < 0){

        perror("[WARN] No file found matching URI.\n");

        handle_404(asock);

        return;

    }

  

    int fd = open(local_uri, O_RDONLY);

    if (fd < 0){

        perror("[ERR] Failed to open file.\n");

        handle_500(asock);

        return;

    }

  

    int ct_len = st.st_size;

    char ct_type[40];

    find_mime(ct_type, local_uri);

    fill_header(header, 200, ct_len, ct_type);

    write(asock, header, strlen(header));

  

    int cnt;

    while((cnt = read(fd,buf, BUF_SIZE)) > 0)

        write(asock, buf, cnt);

}
```

200, 404, 500번 대의 [[상태 코드]]가 구현되어있습니다.

[[컴퓨터 공학/인터넷/네트워크/소켓통신/소켓 통신]]에서도 설명하지만
보면 클라이언트가 서버에게 파일을 요청하면 서버가 해당 위치에 파일이 있는지 확인한 후
상태코드와 함께 파일을 전송합니다.
write로 전송하는데 소켓을 일종의 파일 같은 거라 생각한 거라 보면 됩니다.