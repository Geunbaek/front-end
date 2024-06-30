---
description: XML-like systax extension to ECMAScript
---

# JSX

### JSX

* XML 처럼 작성된 부분을 `React.createElement` 을 쓰는 코드로 변환한다. 중괄호를 사용해서 JavaScript 코드를 그대로 쓸 수 있고, 결국 JavaScript 코드와 1:1로 매칭된다.
* 변환기 중 가장 유명한 Babel로 확인이 가능하다.
  * [https://babeljs.io/repl](https://babeljs.io/repl#?browsers=defaults%2C%20not%20ie%2011%2C%20not%20ie\_mob%2011\&build=\&builtIns=false\&corejs=3.21\&spec=false\&loose=false\&code\_lz=DwEwlgbgfMD07QFBA\&debug=false\&forceAllTransforms=false\&modules=false\&shippedProposals=false\&circleciRepo=\&evaluate=false\&fileSize=false\&timeTravel=false\&sourceType=module\&lineWrap=true\&presets=env%2Creact%2Cstage-2\&prettier=false\&targets=\&version=7.24.7\&externalPlugins=\&assumptions=%7B%7D)
* JSX는 필수가 아니다.&#x20;
* react 17 버전 이후로는 createElemet -> \_jsx 로 변경되었다.

```tsx
// default
<div>Hello, world</div>

React.createElement("div", null, "Hello, world");

<Greeting name="world"/>

React.createElement(Greeting, {
  name: "world"
});

<Button type="button">name</Button>

React.createElement(Button, {
  type: "button"
}, "name");

<Button type="submit">
  <span>name</span>
</Button>

React.createElement(Button, {
  type: "submit"
}, React.createElement("span", null, "name"));

<div>
  <div>count : {count}</div>
  <button type="submit" onClick={() => setCount(count + 1)}>Increase</button>
</div>

React.createElement("div", 
  null, 
  React.createElement(
    "div", 
    null, 
    "count : ", count
  ), 
  React.createElement(
    "button", 
    { 
      type: "submit",
      onClick: () => setCount(count + 1)
    }, 
    "Increase"
));

/* @jsx myCreateElement */
<div>Hello, world</div>

myCreateElement("div", null, "Hello, world");
```

### React Element

* createElement 로 반환되는 JavaScript 객체

### VDOM ( Virtual DOM )

> [https://ko.legacy.reactjs.org/docs/faq-internals.html](https://ko.legacy.reactjs.org/docs/faq-internals.html)

* 실제 DOM 과 동기화 ( 재조정 ) 하기 위해 메모리에 트리형태로 저장된 JavaScript 객체 ( React Element)
* 형태과 DOM 과 유사하다. ( 트리형태 )
* 사용 이유
  * 충분히 빠른 속도&#x20;
  * React 의 선언적 API 를 가능하게 한다.
* 최적화 기법
  * [https://ko.react.dev/reference/react/memo#skipping-re-rendering-when-props-are-unchanged](https://ko.react.dev/reference/react/memo#skipping-re-rendering-when-props-are-unchanged)

### React Developer Tools

* 리액트 개발자를 위해 다양한 기능을 제공하는 확장 프로그램
* React Component 의 트리 구조를 확인할 수 있다.
* Highlight updates when components render. 체크 박스를 체크하면 리액트 컴포넌트가 렌더링 될때마다 highlight 되는 기능을 사용할 수 있다.

### 재조정

> [https://ko.legacy.reactjs.org/docs/reconciliation.html](https://ko.legacy.reactjs.org/docs/reconciliation.html)

* 실제 DOM 과 VDOM 을 비교하여 변경된 부분만 실제 화면에 적용하는 작업
* diffing 알고리즘
  * element 의 타입이 다른 경우
  * 같은 타입의 element 의 경우 두 element의 속성을 비교하고 속성만 변경
  * key&#x20;
    * key를 속성으로 주어서 해당 키가 다른 경우
    * key 값으로 인덱스를 사용할 경우 발생할 수 있는 현상
      * [https://codepen.io/pen?\&editors=0010\&layout=left](https://codepen.io/pen?\&editors=0010\&layout=left)



### &#xD;
