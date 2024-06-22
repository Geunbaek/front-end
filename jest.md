---
description: 테스팅 프레임워크
---

# Jest

> Jest 공식문서
>
> [https://jestjs.io/](https://jestjs.io/)

### 예제

#### BDD  ( Behavior-Driven Development )&#x20;

> Describe - Contect - It

* Jest 에서는 Context 를 제공하지 않는다.
  * `const context = describe;`
  * &#x20;추가적인 플러그인 설치
    * `npm i -D jest-plugin-context`
      *   jest.config.js

          ```
          "setupFilesAfterEnv": [
            "jest-plugin-context/setup"
          ]
          ```

```javascript
const add = (num1, num2) => num1 + num2;

// 기본적인 테스트 코드
test('더하기', () => {
  expect(add(1, 2)).toBe(3);
});

// BDD( Behavior-Driven Development 스타일의 테스트 코드 )
// Describe, Context, It
describe("더하기", () => {
  context("1과 2를 더하면", () => {
    it("3을 리턴해야한다.", () => {
      expect(add(1, 2)).toBe(3);
    });
  });
  
  context("0.1과 0.2를 더하면", () => {
    it("0.3을 리턴해야한다.", () => {
      expect(add(0.1, 0.2)).toBe(0.3); // fail
    });
  });
});

```

### React Testing Library

> React Testing Library
>
> [https://testing-library.com/docs/react-testing-library/intro/](https://testing-library.com/docs/react-testing-library/intro/)
>
> jest-dom
>
> [https://testing-library.com/docs/ecosystem-jest-dom/](https://testing-library.com/docs/ecosystem-jest-dom/)

```typescript
// Greeting.tsx
export default function Greeting({name}:{name:string}){
  return <div>Hello, {name}</div>
}

// Greeting.test.tsx
test('Greeting', () => {
  render(<Greeting name="world" />);

  screen.getByText('Hello, world!');
  screen.getByText(/Hello/);
  expect(screen.queryByText(/Hi/)).not.toBeInTheDocument();
});
```

* UI 테스트에 특화된 라이브러리, E2E test 처럼 사용할 수 있다.
* `Front-end Test !== only React`
  * 본질에 집중하지 못하고 너무 많은 테스트를 작성하게 될 위험이 있다.
* [프론트엔드도 테스트를 해야하나요?](https://www.youtube.com/watch?v=-kUmsKRmOnA)
