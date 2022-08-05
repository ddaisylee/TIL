# CORS

## CORS란?

> _추가 HTTP 헤더를 사용하여, **한 출처에서 실행 중인 웹 애플리케이션이 다른 출처의 선택한 자원에 접근할 수 있는 권한을 부여하도록 브라우저에 알려주는 체제**_ -MDN

## CORS가 나오게 된 배경

### SOP

- SOP(Same Origin Policy, 동일 출처 정책)

- **같은 출처의 리소스만 공유 가능하다는 것을 의미하는 브라우저 정책**

- 여기서 출처는 URI(URL)의 **프로토콜, 호스트, 포트**를 포함합니다.

- 즉 SOP는 리소스와 요청하는 곳의 프로토콜, 호스트. 포트 중 하나라도 다르다면 리소스에 접근할 수 없는 정책입니다.

### SOP의 장단점

- 이렇게 서로 다른 출처의 리소스를 제한하면 해킹 등의 위협으로부터 보호할 수 있었습니다.

- 하지만 다른 출처의 리소스에 접근하는 경우가 그렇지 않은 경우보다 훨씬 많습니다.

> _예를 들어 외부 API를 사용하는 것도 출처가 다르고, 클라이언트 및 서버를 각각 개발하는 것 또한 개발 환경이 다르기 때문에 서로 다른 출처가 됩니다._

## CORS 개념

- CORS(Cross Origin Resource Sharing, 교차 출처 리소스 공유)

- **다른 출처의 자원에 접근할 수 있도록 하는 메커니즘**

> **🙋‍♀️ 그럼 SOP는 안 쓰는건가요?**

> 👉 아닙니다. SOP는 브라우저에서 준수하는 정책입니다. 따라서 브라우저는 SOP에 의해 기본적으로 다른 출처의 리소스 공유를 막지만, CORS를 사용해 특정 리소스에 대한 접근 권한을 얻는 것입니다.

- 구체적으로 서버 응답 헤더에 `'Access-Control-Allow-Origin'`을 통해 접근 권한을 얻습니다.

## CORS의 동작 방식

### 1. 프리플라이트 요청(Preflight Request)

- 실제 요청을 보내기 전에 사전 요청을 보내는 것 (Preflight: 사전 전달)

- `OPTIONS` 메서드를 통해 해당 출처의 리소스에 접근 권한이 있는지 미리 사전에 확인합니다.

- 서버 응답 헤더로 `'Access-Control-Allow-Origin'`으로 출처가 돌아오면 실제 요청을 보냅니다.

- 만약 접근 권한이 없다면 CORS 에러를 띄우고 실제 요청은 전달되지 않습니다.

> `Access`: 접근/`Control`: 제어/`Allow`: 허가/`Origin`: 출처 👉 **접근 및 제어가 허가된 출처!**

### 2. 단순 요청(Simple Requese)

- 특정 조건을 모두 만족하면 프리플라이트 요청을 생략하고 요청을 보내는 것

- 다만 아래와 같은 조건을 모두 만족하는 경우는 많지 않습니다.

  - `GET, HEAD, POST` 요청 중 하나여야 합니다.
  - 자동으로 설정되는 헤더 외에, `Accept, Accept-Language, Content-Language, Content-Type` 헤더의 값만 수동으로 설정할 수 있습니다.
  - `Content-Type 헤더에는 application/x-www-form-urlencoded, multipart/form-data, text/plain` 값만 허용됩니다.

### 3. 인증 정보를 포함한 요청(Credentialed Request)

- 요청 헤더에 인증 정보를 함께 담아 전달하는 것

- 인증 정보는 민감한 정보이기 때문에 클라이언트, 서버 모두 별도의 CORS 설정이 필요합니다.

  - 클라이언트: 요청 헤더에 `withCredentials : true` 를 넣어줘야 합니다.

  - 서버: 응답 헤더에 `Access-Control-Allow-Credentials : true` 를 넣어줘야 합니다.

## ❗️ 3줄 요약

- 브라우저는 동일 출처 정책에 의해 다른 출처의 리소스에 접근하는 것을 제한한다.

- 출처란 URI(URL)의 프로토콜, 호스트, 포트를 의미한다.

- 만약 출처가 다른 리소스를 사용하고 싶으면 다른 출처에 대한 접근 권한을 얻는 메커니즘인 CORS를 설정한다.

## 📕 참고 자료

[동일 출처 정책](https://developer.mozilla.org/ko/docs/Web/Security/Same-origin_policy)

[교차 출처 리소스 공유 (CORS)](https://developer.mozilla.org/ko/docs/Web/HTTP/CORS)
