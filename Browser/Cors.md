# Cors

## CORS(Cross-Origin Resource Sharing, 교차 출처 리소스 공유)

CORS는 웹 페이지가 다른 도메인의 서버에서 데이터를 요청할 때, 그 요청이 안전한 출처인지 확인하기 위해 사용이 된다.

출처가 한가지라도 다르면, cors error가 난다.

## SOP (Same Origin Policy)

SOP는 웹 페이지가 동일 출처의 리소스에 대한 요청을 허용하지만, 다른 출처의 리소스에 대한 요청은 대부분 차단합니다.

즉 같은 출처로만 요청을 보낼 수 있다.

## Origin

Origin은 출처라는 표현으로 Protocol + hostname + port가 합쳐진 개념이다.

![과정1](https://static.tosspayments.com/docs/glossary/cors-url.png)

## CORS 에러 해결하기

### 1. Access-Control-Allow-Origin

서버에서 Access-Control-Allow-Origin를 설정해준다.

`'Access-Control-Allow-Origin': <origin> | *`

### 2. 프록시를 이용해서 CORS를 해결

프록시를 사용하면, 웹 애플리케이션이 리소스와 동일한 출처에서 요청을 보내는 것처럼 보이게 해준다. 브라우저가 서버에 직접적으로 요청하는게 아니라 중간에 프록시를 이용해서 중계 기능을 하는 것이다.

```
/** @type {import('next').NextConfig} */
const nextConfig = {
  reactStrictMode: true,
  swcMinify: true,
  async rewrites() {
    return [
      {
        source: "/:path*",
        destination: "(API 주소)/:path*",
      },
    ];
  },
};
module.exports = nextConfig;
```

nextjs 설정에서 rewrites 기능을 사용해서 cors에러를 해결 할 수 있다.

`source` 같은 경우에 우회할 경로(마스킹) 주소를 넣어주면 되고

`destination` 에 실제 API 주소를 넣어주면 된다.

결론, CORS 에러가 나면, 두 출처가 서로 다르다는 의미이고,
CORS 설정을 해주면 출처가 `다른 서버간의 리소스 공유`를 허용해준다는 뜻이라는걸 다시 알게 되었다.

출처 ) https://docs.tosspayments.com/resources/glossary/cors
