---
description: 사용자 인터페이스를 만들기 위한 라이브러리
---

# React

> 리액트 공식문서
>
> [https://react.dev/](https://react.dev/)

* [React as a UI Runtime](https://overreacted.io/react-as-a-ui-runtime/)

### 렌더링

```typescript
import ReactDOM from "react-dom/client";

function App(props: { count: number }) {
  return (
    <>
      count {props.count}
      <input />
    </>
  );
}

function main() {
  const element = document.getElementById("root");

  if (!element) {
    return;
  }

  const root = ReactDOM.createRoot(element);

  let count = 0;

  root.render(<App count={count} />);

  setInterval(() => {
    count += 1;
    root.render(<App count={count} />);
  }, 1_000);
}
main();

```

* 리액트는 UI의 변경된 부분만 업데이트 한다.
  * render 를 여러번 하더라도 react 는 변경된 부분만 업데이트 하기 때문에 input 의 값은 변경되지 않는다.
  * [https://react.dev/reference/react-dom/client/createRoot#updating-a-root-component](https://react.dev/reference/react-dom/client/createRoot#updating-a-root-component)
* 리액트의 렌더링
  * VDOM 업데이트 -> DOM 업데이트
  * VDOM
    * VDOM 이 업데이트 되면 이전의 VDOM 스냅샷과 비교한 뒤 실제 DOM 에서 변경된 내용만 업데이트 한다. ( diffing )
* [React는 컴포넌트를 언제 다시 리렌더링 할까요?](https://megaptera.notion.site/React-c5911858618c47d2bd716718721bff6d)
* [왜 리액트에서 리렌더링이 발생하는가](https://megaptera.notion.site/b2100b92619841cbaf3c5cc69cc3168b)
* [React 렌더링 동작에 대한 (거의) 완벽한 가이드](https://megaptera.notion.site/React-2b0bebf44f70424cb8ed338e59f4e431)

### 리액트는 프레임워크인가? 라이브러리인가?

* 제어의 역전(IoC: Inversion of Control)이 Framework의 주요한 특징이고, React는 IoC를 통해 상태와 업데이트가 얽힌 복잡한 상황을 간단히 선언형 UI로 구성하는 혜택을 누린다.&#x20;
* [제어의 역전](typescript.md)
