# storybook

## CDD

- CDD는 Component Driven Development, 컴포넌트 주도 개발입니다.

- CDD는 마치 레고를 조립하듯이 부품 단위로 결합하여 UI 컴포넌트를 개발하는 방식을 의미합니다.

- 컴포넌트 단위로 UI를 개발하면 재사용과 유지보수에 유리합니다.

- storybook은 React로 CDD를 할 수 있는 도구 중 하나입니다.

## storybook이란

> Storybook is an open source tool for building UI components and pages in isolation. It streamlines UI development, testing, and documentation.

- storybook은 컴포넌트와 페이지를 독립적으로 개발하기 위한 툴입니다.

- storybook은 UI 개발, 테스트, 문서화를 쉽게 해줍니다.

- 스토리(story)라고 부르는 컴포넌트의 미리보기를 생성해 여러 개의 스토리들을 만들어 컴포넌트를 개발합니다.

## storybook의 장점

- 개별 컴포넌트를 복잡한 애플리케이션 로직으로 부터 분리해 실시간으로 결과물을 확인할 수 있습니다.

- 컴포넌트 리팩토링 효과를 가져옵니다.

> **🙋‍♀️ storybook으로 어떻게 리팩토링이 가능한건가요?**

> 👉 컴포넌트를 스토리로 옮길 때 어려움이 있다면 컴포넌트 설계의 결함에 대해 생각하게 되고, 이를 통해 컴포넌트를 재사용이 쉽게 리팩토링하는 부수적인 효과를 얻을 수 있습니다. (출처: [스토리북 작성을 통해 얻게 되는 리팩토링 효과](https://fe-developers.kakaoent.com/2022/220609-storybookwise-component-refactoring/))

## 기본 사용 방법

- Title이라는 컴포넌트의 스토리를 생성하는 예제입니다.

### Title 컴포넌트 생성

```jsx
// scr/Title.js

// title과 textColor 데이터를 props로 받습니다.
const Title = ({ title, textColor }) => {
  return <h1 style={{ color: textColor }}>{title}</h1>;
};

export default Title;
```

### 스토리 생성

- 스토리를 만들기 위해 `Title.stories.js`파일을 생성합니다.

- `컴포넌트명.stories.js`로 파일명을 지으면 storybook이 이를 해당 컴포넌트의 스토리로 인식합니다.

```jsx
// src/Title.stories.js

// 1. 스토리를 만들 컴포넌트를 불러옵니다.
import Title from "./Title";

// 2. 문서화하는 컴포넌트에 대한 정보를 storybook에게 알려주기 위해 export default합니다.
export default {
  // 컴포넌트를 참조하는 방법
  title: "Practice/Title",
  // 참조하는 해당 컴포넌트
  component: Title,
  // 컴포넌트가 전달받는 argument의 종류와 타입
  argTypes: {
    title: { control: "text" },
    textColor: { control: "text" },
  },
};

// 3. 템플릿을 생성해줍니다.
const Template = (args) => <Title {...args} />;
```

### 템플릿을 바인드하는 방식

- 생성한 템플릿과 만들 스토리를 바인딩한 다음 `args`를 전달합니다.

```jsx
// 스토리를 하나 만듭니다. 이를 위해 템플릿과 bind한 다음 args를 전달해줍니다.
// Function.prototype.bind(): 함수의 복사본을 만드는 메서드
// -> 컴포넌트 또한 함수이기 때문에 bind로 생성
export const RedTitle = Template.bind({});

// 만든 스토리에 args를 전달합니다.
RedTitle.args = {
  title: "Red Title",
  textColor: "red",
};

// 비교를 위해 다른 스토리를 하나 더 만들어주었습니다.
export const BlueTitle = Template.bind({});

// 마찬가지로 생성한 스토리에 args를 전달합니다.
BlueTitle.args = {
  title: "Blue Title",
  textColor: "blue",
};
```

### 직접 args를 전달받는 방식

- 스토리를 템플릿과 바인딩하지 않고 스토리에서 직접 `args`를 전달합니다.

```jsx
export const StorybookTitle = (args) => {
  return <Title {...args} />;
};
```

## styled-components와 함께 사용하는 방법

- 또다른 CDD 도구인 stlyed-components와 함께 사용할 수 있습니다.

- styled-components를 사용한 Button 컴포넌트의 스토리를 생성하는 예제입니다.

### Button 컴포넌트 생성

```jsx
import styled from "styled-components";

const StyledButton = styled.button`
  background: ${(props) => props.color || "white"};
  width: ${(props) => (props.size === "big" ? "200px" : "100px")};
  height: ${(props) => (props.size === "big" ? "80px" : "40px")};
`;

const Button = ({ color, size, text }) => {
  return (
    <StyledButton color={color} size={size}>
      {text}
    </StyledButton>
  );
};

export default Button;
```

### 스토리 생성

- 템플릿 바인딩이 아닌 직접 args를 전달받는 방식을 적용해보겠습니다.

```jsx
import Button from "./Button";

export default {
  title: "Practice/Button",
  component: Button,
  argTypes: {
    color: { control: "color" },
    size: { control: { type: "radio", options: ["big", "small"] } },
    text: { control: "text" },
  },
};

export const StorybookButton = (args) => {
  return <Button {...args}></Button>;
};
```

## ❗️ 3줄 요약

- storybook은 컴포넌트를 독립적으로 개발하도록 도와주는 툴이다.

- 스토리라는 컴포넌트의 미리보기를 통해 여러 스토리들(여러 버전들)을 만들 수 있다.

- 크게 `컴포넌트 불러오기 -> 컴포넌트 정보 내보내기 -> 템플릿 생성 -> 스토리 생성`의 과정을 거친다.

## 📕 참고 자료

[Storybook Docs](https://storybook.js.org/)
