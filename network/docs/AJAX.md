# AJAX

## AJAX란?

- Asynchronous JavaScript And XMLHttpRequest

- 자바스크립트와 XML을 이용한 비동기적인 정보 교환 방법

- 웹 페이지에 필요한 데이터를 비동기적으로 받아와 화면에 출력할 수 있습니다.

## AJAX를 활용한 대표적인 기능

### 추천 검색어

- 사용자가 텍스트를 입력할 때마다 입력 텍스트로 시작하는 단어를 비동기적으로 받아와 표시합니다.

### 무한 스크롤

- 사용자가 페이지 스크롤을 하면서 페이지 바닥에 닿을 때마다 fetch를 통해 데이터를 받아옵니다.

## 핵심 개념

### Fetch

- 비동기적으로 서버에 요청을 보내는 방식

- 따라서 응답을 받을 때까지 기다리지 않고 사용자가 계속 페이지를 사용할 수 있습니다.

- 이전에는 XMLHttpRequest라는 객체를 사용해 비동기적으로 데이터를 받아왔습니다.

- 하지만 XHR의 문제점과 Fetch API의 여러 장점으로 인해 현재는 Fetch API를 사용합니다.

### DOM

- 또한 자바스크립트를 이용한 DOM 조작이 가능하므로, Fetch를 통해 받아온 데이터를 기존 페이지에 추가할 수 있습니다.

- 따라서 새로운 페이지를 로드하지 않고도 기존 페이지에 필요한 부분만 변경하여 데이터를 표시할 수 있습니다.

## 장점

### 빠른 페이지 전환

- 서버에서 HTML 파일을 보내주지 않아도 필요한 데이터를 비동기적으로 가져와 일부분만 업데이트합니다.

- 따라서 웹페이지 전환 속도가 온전한 HTML을 보내서 업데이트하는 것보다 빠릅니다.

- 빠르게 렌더링할 수 있기 때문에 사용자와 더 많이 상호작용이 가능한 애플리케이션을 개발할 수 있습니다.

### 작은 데이터 크기

- 필요한 데이터를 텍스트 형태(JSON, XML 등)로 보내면 되기 때문에 데이터의 크기가 비교적 작습니다.

### 표준화된 방법

- XHR이 표준화된 이후 브라우저에 관계없이 AJAX를 사용할 수 있습니다.

## 단점

### SEO

- AJAX 방식의 웹 애플리케이션은 HTML을 한 번 받아온 후 서버에서 비동기적으로 필요한 데이터를 가져와 렌더링합니다.

- 처음 받는 HTML 파일에는 데이터를 채우기 위한 틀만 작성되어 있는 경우가 많습니다. 따라서 검색 엔진에 충분한 정보를 제공하지 못합니다.

## ❗️ 3줄 요약

- AJAX는 데이터를 비동기적으로 받아오는 방식을 의미한다.

- Fetch API 이전에는 XMLHttpRequest를 사용했지만, 현재는 Fetch API를 이용한다.

- 필요한 데이터만 비동기적으로 받아오기 때문에 HTML을 받아오는 것보다 페이지 전환이 빠르지만, SEO에 불리하다.

## ❓ 질문

- XMLHttpRequest의 단점과 Fetch API의 장점이 정확하게 어떤 것이고, 어떻게 다를까?

- 현재는 XML보다 JSON 형식으로 데이터를 주고 받는데, 어떤 단점과 장점이 있고, 어떻게 다를까?

## 📕 참고 자료

[Fetch 사용하기 - MDN](https://developer.mozilla.org/ko/docs/Web/API/Fetch_API/Using_Fetch)

[XMLHttpRequest - MDN](https://developer.mozilla.org/ko/docs/Web/API/XMLHttpRequest)

### 참고하면 좋은 자료

[초보자를 위한 XML 설명](https://support.microsoft.com/ko-kr/office/%EC%B4%88%EB%B3%B4%EC%9E%90%EB%A5%BC-%EC%9C%84%ED%95%9C-xml-%EC%84%A4%EB%AA%85-a87d234d-4c2e-4409-9cbc-45e4eb857d44)

[JSON과 XML](http://www.tcpschool.com/json/json_intro_xml)
