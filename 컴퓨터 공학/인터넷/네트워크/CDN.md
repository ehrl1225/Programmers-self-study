# Content Delivery Network

컨텐츠를 좀 더 빠르게 제공하기 위해서 여기저기 서버를 두는 것 
서버를 싹 다 복사하는건 미러 서버고
캐시해서 저장한다고 함
DNS에 요청을 해서 가장 빠르게 접속이 가능한 위치로 연결되게 한다.
이 CDN서버들을 Edge라고 함

정적 캐싱은 미리 데이터를 넣어두는 방식
동적 캐싱은 사용자가 요청할 때마다 넣는 방식

TTL(Time To Live) 데이터를 캐시에 얼마나 남아있게 할지도 정할 수 있다.

본 서버에 주어지는 과부하가 줄어듬

DDOS를 받더라도 CDN이 대신 맞아주게 할 수 있음


# 전송속도
물리적 거리를 얼마나 빠르게 이동하는가

# 처리량
데이터를 얼마나 많이 보내는 가
