# HTTP 기초

## HTTP 메시지

- 클라이언트와 서버가 데이터를 교환하는 방식

- 클라이언트에서 보내는 HTTP 요청과 서버에서 보내는 HTTP 응답 메시지가 있습니다.

![](https://developer.mozilla.org/en-US/docs/Web/HTTP/Messages/httpmsgstructure2.png)

## HTTP 요청 메시지의 구조

### Start Line

- 클라이언트에서 서버로 보내는 정보입니다. 다음 3가지 요소를 전달합니다.

- HTTP 메서드

- 요청 URI

- HTTP 프로토콜 버전

### Headers

- `Header Name: Header Value` 형태의 헤더들의 집합

### Empty Line

- 헤더와 본문을 구분하는 빈 줄

### Body

- 요청과 관련된 데이터 또는 문서

![](https://developer.mozilla.org/en-US/docs/Web/HTTP/Messages/http_request_headers3.png)

## HTTP 응답 메시지의 구조

### Status Line

- 서버에서 클라이언트로 보내는 정보

  - HTTP 프로토콜 버전

  - 상태 코드

  - 상태 코드를 나타내는 텍스트

### Headers

- `Header Name: Header Value` 형태의 헤더들의 집합

### Empty Line

헤더와 본문을 구분하는 빈 줄

### Body

- 응답 리소스 데이터이며, 상태코드에 따라 body가 존재하지 않을 수도 있습니다.

![](https://developer.mozilla.org/en-US/docs/Web/HTTP/Messages/http_response_headers3.png)
