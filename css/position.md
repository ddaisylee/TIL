# position

## absolute

### absolute는 절대적이지 않습니다.

- 처음 `absolute`를 접할 때는 `absolute`라는 단어가 가지는 뜻 때문에 혼란을 가져올 수 있습니다.

- 즉 하나의 절대적인 기준이 있는 것처럼 생각되기 쉽습니다.

- 하지만 `absolute`는 상위 요소를 기준으로 상대적으로 배치되며, 상황에 따라 기준이 되는 상위 요소도 달라집니다.

> **🙋‍♀️ 그럼 왜 absolute라고 하는건가요? 상대적이면서…**

> 👉 가장 가까운 상위 요소를 배치 기준으로 정하는 것 뿐이지, 자신이 가지고 있던 기존의 맥락에서는 완전히 독립적으로 움직입니다. 마치 상대 경로는 현재 위치를 기준으로, 절대 경로는 루트를 기준으로 경로를 설정하는 것과 같습니다. 즉 `absolute`는 절대 경로의 루트처럼 자신의 상위 요소가 있고 이를 기준으로 배치된다는 점에서 비슷합니다. 이러한 이유로 `absolute`라는 이름이 붙지 않았을까요? 자신의 원래 맥락에서 제외되어 자신이 배치될 요소를 찾아 그것을 절대적인 기준으로 삼는 것이죠. (이해를 돕기 위한 예시이며, 정확하지 않습니다.)

### absolute가 배치 기준을 정하는 방법

- `absolute` 그 이름과는 사뭇 다르게 상위 요소에 따라 배치 기준을 정합니다.

- 그렇다고 해서 바로 위에 있는 요소가 상위 요소가 되는 것은 아닙니다.

- 다음과 같은 기준으로 상위 요소를 결정합니다.

  1. `position: static`이 아닌 상위 요소를 찾는다.

  2. 만약 `position: static`이 아닌 상위요소를 찾을 수 없으면, `body`가 상위요소가 된다.

- 따라서 이러한 특성을 바탕으로 가설을 세워 직접 코드로 확인해볼 수 있습니다.

  - `position: static`이 아닌 상위 요소를 기준으로 배치된다.

  - 만약 `position: static`이 아닌 상위 요소가 없다면, `body`를 기준으로 배치된다.

## absolute 실습

[position-absolute - 코드샌드박스](https://codesandbox.io/s/absolute-practice-x4tpr4)

## ❗️ 3줄 요약

- `position: absolute` 속성은 요소가 문서의 흐름에서 벗어나 상위 요소를 기준으로 배치한다.

- 이때 `position: static`이 아닌 가장 가까운 상위 요소가 기준이 된다.

- 만약 `position: static`이 아닌 상위 요소가 없으면 `body`가 기준이 된다.

## 📕 참고 자료

[position - MDN](https://developer.mozilla.org/ko/docs/Web/CSS/position)

[CSS의 position 속성으로 HTML 요소 배치하기](https://www.daleseo.com/css-position/)
