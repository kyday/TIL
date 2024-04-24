# HTTP / HTTPS

## HTTP(Hypertext Transfer Protocol)

서버와 클라이언트간에 메세지를 교환 하는 통신 규약이다.

## HTTPS(Hypertext Transfer Protocol Secure)

HTTP에서 보안이 강화된 버전이라고 볼 수 있다. SSL 또는 TLS 프로토콜을 사용해 데이터를 암호화하고
안전하게 전송해 중요한 정보가 도난당하거나 조작되는것을 방지해준다.

## SSL(Secure Socket Layer) / TLS(Transport Layer Security)

네트워크 상에서 보안 통신을 제공하기 위한 프로토콜이다.
초기에 SSL은 넷스케이프에 의해 개발되었고 후속 버전으로 TLS가 개발이 되었습니다.

## 대칭키(Symmetric key)

대칭키 암호화는 '하나의 키(key)' 를 사용해 암호화 또는 복호화를 한다.

- 장점으로는 비대칭키보다 속도가 빠르다.
- 단점으로는 대칭키가 탈취당하면 문서가 노출되고 변형이된다.

## 비대칭키(= 공개키, 개인키)

공개키와 대칭키로 각각 암호화 또는 복호화를 할 수 있다.

공개키 -> 암호화한 텍스트 -> 개인키로 복호화를 할 수 있다.
다른 키로 복화화를 할 수 없다.

## SSL/ TLS 작동 과정

1. Client Hello: 클라이언트가 서버에게 요청 연결 시도
2. Server Hello: 클라이언트에서 `Client Hello`요청을 받고, 인증서(공개키가 들어있음)와 같이 응답한다. (서버 -> 클라이언트)

3. ClientKeyExchange : 브라우저는 서버의 인증서가 신뢰가 있는지 확인하는 과정이다.
   클라이언트 난수 + 서버 난수 = 세션 키(또는 Premaster secret)를 생성하고 그 키를 서버의 공개 키를 사용하여 암호화해서 보낸다.

4. SSL/ TLS HandShake 종료: Handshake가 완료되면 클라이언트와 서버는 안전한 통신을 위해 암호화된 데이터를 주고받을 수 있게 됩니다.

\*\* 대칭키와 공개키 방식 모두 사용하는 이유가 공개키 방식으로만 하면 웹 서버와 브라우저에 많은 부담이 되기 때문에 HandShake 과정에서는 공개키 방식을 사용하고 그 이후는 HTTPS 통신은 대칭키 방식을 사용한다.

![과정](https://velog.velcdn.com/images/bbkyoo/post/cdc237f0-d57a-46cb-a4c4-c14dfe11639b/image.png)
