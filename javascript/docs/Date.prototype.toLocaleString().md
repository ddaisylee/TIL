# toLocaleString()

- `Date.prototype.toLocaleString(locales, [options])`

- 날짜를 읽기 쉬운 문자열로 변환하는 메서드입니다.

- `locale`과 `opitons` 파라미터를 받을 수 있습니다.

## locales

- 변환할 언어를 지정하는 파라미터입니다.

- BCP 47이라는 언어 태그(언어 코드)를 사용합니다.

```js
toLocaleString(en-US) // 영어-미국
toLocaleString(ko-KR) // 한국어-대한민국
toLocaleString(ja-JP) // 일본어-일본
...
```

## options

- 포맷, 즉 표현 형식을 지정하는 객체를 받는 파라미터입니다.

- 예를 들어 `month`는 아래와 같은 포맷 속성을 지정할 수 있습니다.

![](https://velog.velcdn.com/images/ddaisylee/post/542301eb-3f9f-4a3b-9002-e12113328a8d/image.png)

- 더 많은 속성은 [Intl.DateTimeFormat() constructor - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/DateTimeFormat/DateTimeFormat)에서 확인할 수 있습니다.

- `toLocaleString()`을 사용해 년, 월, 일의 표현을 아래와 같이 지정할 수 있습니다.

```js
// 작성 날짜를 기준으로 예시를 들겠습니다.
const date = new Date();

console.log(date); // Sun Jul 17 2022 13:58:44 GMT+0900 (한국 표준시)

const year = date.toLocaleString('en-US', {year: "numeric"});
const month = date.toLocaleString('en-US', {month: 'long'});
const day = date.toLocaleString('en-US', {day: '2-digit'};

console.log(year); // '2022'
console.log(month); // 'July'
conosole.log(day); // '17'
```

> ⭐️ **변환한 값은 모두 문자열입니다.** 속성이 `'numeric'`이라고 해서 값이 숫자 타입이라고 헷갈리지 않도록 합니다. (메서드의 이름 자체가 'to String', 즉 문자열로 바꾼다는 의미를 포함한다는 걸 기억하면 좋을 것 같습니다.)

```js
console.log(typeof year); // 'string'
console.log(typeof month); // 'string'
console.log(typeof day); // 'string'
```

## 리액트에 적용하기

- 다음과 같은 방법으로 리액트에 간단하게 적용해보았습니다.

  [toLocaleString() 실습 - codesandbox](https://codesandbox.io/s/tolocalestring-jeoy4k?file=/src/App.js)

```jsx
import "./styles.css";

export default function App() {
  const date = new Date();

  const year = date.toLocaleString("en-US", { year: "numeric" });
  const month = date.toLocaleString("en-US", { month: "long" });
  const day = date.toLocaleString("en-US", { day: "2-digit" });
  return (
    <div className="App">
      <div>년, 월, 일을 여기에 표시합니다.</div>
      <div>
        {year} {month} {day}
      </div>
    </div>
  );
}
```

## ❗️ 3줄 요약

- `Date.toLocaleString()`은 날짜를 읽기 쉬운 형식으로 커스텀할 수 있는 메서드다.

- 첫 번째 파라미터(`locales`)는 표현할 언어를 지정하는 언어 코드다.

- 두 번째 파라미터 (`options`) 는 표현 형식을 지정하는 객체다.

## ❓ 질문

- Date 형식을 표현하는 메서드가 다양한 것 같은데, 다른 메서드는 없을까?

## 📕 참고 자료

[Date.prototype.toLocaleString() - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/toLocaleString)

[BCP 47 Language Codes List](https://appmakers.dev/bcp-47-language-codes-list/)
