모든 네트워크와 연결되는 프로그램은 소켓을 통해 통신한다.
따라서 [[컴퓨터 공학/인터넷/네트워크/소켓통신/소켓 통신]]에 대해서 알아야 한다.
[[C]]로 만드니 [[C]]에 대한 지식도 가져야 한다.

우분투에서 돌린 것입니다.
헤더파일이랑 CMakeLists.txt파일은 생략되었습니다.

# common
헤더 파일을 일단 정의 해두려 한다.
[[C HTTP common.h]]

# main
시작 부분이다.
[[C HTTP main.c]]

# http_functions
http 관련 작업을 합니다.
[[C HTTP http_functions.c]]

# my_thread
각 클라이언트의 스레드에서 동작하는 코드입니다.
[[C HTTP my_thread.c]]

