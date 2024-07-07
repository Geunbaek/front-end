# 리액트로 사고하기

> 리액트로 사고하기
>
> [https://ko.react.dev/learn/thinking-in-react](https://ko.react.dev/learn/thinking-in-react)

### REST API

> REST( Representational State Transfer ) 아키텍처 스타일의 설계 원칙을 준수하는 _API_

#### 설계 원칙

* 균일한 인터페이스
  * 동일한 리소스에 대한 모든 api 요청은 요청의 출처에 관계없이 동일하게 표시되어야 한다.
* 클라이언트 - 서버 분리
  * 클라이언트 및 서버 애플리케이션은 완전히 독립적이어야 한다.
* 무상태
  * 무상태성이기에 각 요청에는 처리에 필요한 모든 정보가 포함되어야 한다.
* 캐시 가능성
  * 가능한 경우 클라이언트나 서버측에서 리소스를 캐시할 수 있어야한다.
* 계층화된 시스템 아키텍처
  * 클라이언트나 서버가 최종 애플리케이션과 통신하는지 중개자와 통신하는지 알 수 없도록 설계해야한다.
*  코드 온 디멘드
  * 정적 리소스를 전송하지만 경우에 따라 응답에 대한 실행 코드가 포함될 수 있다.
  * 이 경우 코드는 온 디맨드 방식으로만 실행되어야한다.

#### 구성 요소

* 자원 ( Resource ) : HTTP URI
* 자원에 대한 행위 ( Verb ) : HTTP Method
  * Create ( POST )
  * Read ( GET )
  * Update ( PUT, PATCH )
    * PUT : 자원 전체 교체
    * PATCH : 자원 부분 교체
  * Delete ( DELETE )
* 자원에 대한 행위 내용 (  Representations ) : HTTP Message Pay Load

### GraphQL

> API 를 위한 쿼리 언어이자 서버측 런타임으로 클라이언트에게 요청한 만큼의 데이터를 제공하는데  우선 순위를 둔다.

#### 특징

* 하나의 엔드포인트에 다른 쿼리를 사용하여 요청
* 원하는 응답 값만 받을 수 있다.

구성 요소

* Read ( Query )
* Command: Create, Update, Delete ( Mutation )
* Subscribe ( Event )

### JSON ( JavaScript Object Notation )

> 속성-값 쌍, 배열 자료형 또는 기타 모든 시리얼화 가능한 값 또는 키-값 쌍으로 이루어진 데이터 오브젝트를 전달하기 위해 인간이 읽을 수 있는 텍스트를 사용하는 개방형 표준 포맷

### 명령형 프로그래밍 vs 선언형 프로그래밍

#### 명령형 프로그래밍 ( HOW )

> 선언형 프로그래밍과 반대되는 개념으로, 프로그래밍의 상태와 상태를 변경시키는 구문의 관점에서 연산을 설명하는 프로그래밍 패러다임

#### 선언형 프로그래밍 ( WHAT )

> 어떤 방법으로 해야 하는지를 나타내기보다 무엇과 같은지 설명하는 경우 "선언형" 이라고 한다.

```typescript
// 명령형
const nums = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
const doubleNums = [];

for (let i = 0; i < nums.length; i++) {
  doubleNums.push(nums[i] * 2);
}

// 선언형
const nums = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
const doubleNums = nums.map(num => num * 2);
```

### Step 1 : UI를 컴포넌트 계층으로 쪼개기  <a href="#step-1-break-the-ui-into-a-component-hierarchy" id="step-1-break-the-ui-into-a-component-hierarchy"></a>

* 간단한 컴포넌트를 모아 복잡한 UI 만든다.
* 컴포넌트를 나누는 기준
  * SRP ( Single Responsibility Principle ) : 단일책임원칙
    * 컴포넌트가 너무 커진다면 분리
  * CSS ( class name 으로 나누었던 기준과 같이 )
  * Design's Layer ( 디자인에서 사용된 계층 그대로 )
  * information Architecture ( JSON Schema 의 영향 )
    * 실제로 많이 사용
    * 자연스러운 SRP를 위해 강제됨
* 단계
  * 코드를 길게 작성
  * 적절하게 자를 수 있는 부분이 보일 때 컴포넌트로 추출한다.
    * 바로 다른 파일로 분리 해야한다는 생각 X
  * 컴포넌트를 나누는 기준이 애매하면 다시 하나의 컴포넌트로 합쳤다가 다시 나누어 줘도 무방하다.

### Step 2 : React로 정적인 버전 구현하기  <a href="#step-2-build-a-static-version-in-react" id="step-2-build-a-static-version-in-react"></a>

* 상호작용이 없는 정적인 페이지를 구현한다.
* 프로젝트가 커지면 상향식으로 만들고 테스트를 작성하면서 개발하는 것이 더 효율적이다.

### Step 3: 최소한의 데이터만 이용해서 완벽하게 UI State 표현하기  <a href="#step-3-find-the-minimal-but-complete-representation-of-ui-state" id="step-3-find-the-minimal-but-complete-representation-of-ui-state"></a>

#### State&#x20;

* `변경`을 다루기 위한 요소
* 아무렇게나 막 만들어도 동작은 하나, 일관성과 효율을 위해 DRY 원칙을 따르는 SSOT를 만든다.
* 변경이 되야한다. 변경되지 않는건 state로 관리할 필요가 없다.
* 부모 컴포넌트가 props를 통해 전달한다면 state가 아님
* 다른 state나 props를 이용해 계산 가능하다면 state가 아님
* 불필요한 state 관리로 effect를 사용하지 마라!
  * [**https://ko.react.dev/learn/you-might-not-need-an-effect**](https://ko.react.dev/learn/you-might-not-need-an-effect)

#### DRY ( Don't Repeat Yourself )

> 중복 배재
>
> 모든 형태의 정보 중복을 지양하라는 원리

#### SSOT ( Single Source of Truth )

> 정보 모형과 관련된 데이터 스키마를 모든 데이터 요소를 한 곳에서만 제어 또는 편집하도록 조직

#### 상태를 어디서 관리해야하나?

* 해당 상태에 의존적인 모든 컴포넌트의 최상위 컴포넌트에서 관리해야함.
*   상태 끌어올리기

    * 자식의 컴포넌트에서 state 제거 & props 에 해당 property 추가
    * 하드코딩된 데이터를 부모 컴포넌트로 전달
    * 공통 부모에 state 를 추가

    > JS 에서는 함수가 일급 객체이므로 state 뿐 아니라 state를 수정하는 콜백함수도 전달이 가능하다



```typoscript
// 일급 함수

// 1. 변수에 함수를 할당 할 수 있다.

const foo =
```

#### &#x20;제어 컴포넌트 vs 비제어 컴포넌트

* 제어 컴포넌트 : 자체 지역 state 대신 props 에 의해 제어되는 컴포넌트
* 비제어 컴포넌트 : 지역 state를 갖는 컴포넌트
