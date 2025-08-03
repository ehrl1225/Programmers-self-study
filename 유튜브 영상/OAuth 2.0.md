다른 웹의 계정을 통해 로그인하는 것은 좋은 보안성을 가지는데
그러려면 내 서버에서 다른 유저의 다른 사이트 계정 정보를 가져야 하는데
이는 유저의 입장과 다른 사이트 입장에서도 보안적으로 신뢰를 하기 힘들다.
따라서 accessToken을 사용한다.

# 역할
다른 사이트를 Resource Server라고 부른다.
유저는 Resource Owner라고 부른다.
내 서버는 Client라고 부른다.

# 등록
Client가 Resource Owner에게 등록하는 작업이 필요하다.
Resource Owner는 각자 다 다른 값 공통적으로 받는다.
Client ID : 이건 유저 ID 공개되어도 문제가 없지만
Client Secret : 이건 비밀번호로 공개되면 큰일이 발생한다.
Authorized redirect URIs : 리소스 서버에게 이 주소로 Authorized code를 전달해 달라고 전하는 것이다.

# Resource Owner의 승인
클라이언트는 Resource User에게 리소스 서버에 client_id와 scope와 redirect_url이 포함된 링크를 전달해주고
리소스 주인은 리소스 서버에 접속해서 확인을 하고 승인을 하면

# Resource Server의 승인
리소스 서버는 임시 비밀번호인 authorization code를 resource owner에게 전송한다.
그리고 그 authorization code를 통해 client에 접속한다.
클라이언트는 authorization code를 파악하고
resource server에게 client id, client secret, redirect url, authorization code를 보낸다.
resource server는 위 정보가 맞는지 확인하고 승인한다.

# 액세스 토큰 발급
resource server는 client에게 액세스 토큰을 전송한다.
이 후로는 Client가 Resource Server에게 이 액세스 토큰으로 접근하면
user id, scope를 알고 있고 유효한 서비스를 제공한다.

# API 호출
access token을 헤더에 넣어서 전송하는 방법이나 
parameter에 넣어서 사용하는 방법도 존재한다.

# Refresh Token
액세스 토큰을 다시 받기 위해 사용한다.
액세스 토큰을 사용하다가 액세스 토큰이 만료되면
refresh token을 통해 액세스 토큰을 받아서 사용한다.
