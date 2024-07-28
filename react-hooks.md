# React Hooks

> 16.8 버전에 Hooks 가 도입됨
>
> use로 시작하는 함수를 Hook이라 부름

### 기존 방식의 문제점들

1. Wrapper Hell ( [HOC : Higher-Order Components ](https://ko.legacy.reactjs.org/docs/higher-order-components.html))
2. 거대한 컴포넌트

### 기존과 Hook 이후

* 기존
  * 상태가 있는 컴포넌트는 class component props만 사용하는 재사용 가능한 작은 컴포넌트는 Function component로 작성
* 현재
  * Function component 만 사용
  * 상태 관리 유무를 바로 알아차리기에는 힘들어짐 -> 신경쓰지 않아도 된다.
  * 복잡한 요소는 모두 Hook으로 격리 및 재사용 가능

### Hook 규칙

> [https://ko.react.dev/reference/rules/rules-of-hooks](https://ko.react.dev/reference/rules/rules-of-hooks)

1. Hook을 최상위 레벨에서만 호출
   1. Hook을 반복문, 조건문, 중첩함수, 또는 `try / catch / finally` 블록 내부에서 호출 X
2. Hook을 React 함수에서만 호출
   1. React 컴포넌트, 커스텀 Hook 외의 함수에서는 Hook 호출 X

### 대표적인 Hooks

* useState
* useEffect
* useContext
* useRef
* useLayoutEffect

&#x20;&#x20;
