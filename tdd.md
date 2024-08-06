---
description: Test Driven Development
---

# TDD

> 테스트 코드를 먼저 작성하는 즉, 구현보다 인터페이스와 스펙을 먼저 정의함으로써 개발을 진행하는 방식

### TDD Cycle

1. Red -> 실패하는 테스트 코드를 작성. 인터페이스와 스펙에 집중한다.
2. Green -> 재빨리 테스트를 통과한다. 이때 올바른 방법이 아니여도 괜찮다.
3. Refactor -> 리팩터링을 통해 코드를 올바르게 만든다. TDD 에서 가장 중요한 부분이지만 간과될 떄가 많다.

> 작은 단계를 찾고, 코드에서 피드백을 얻는게 중요하다 ! 2번이 어렵다면 1번으로 돌아가서 더 작고 쉬운 문제를 정의한다. 3번을 위해 의도를 드러내고 중복을 찾아 제거하는 연습이 필요하다. 이 둘이 익숙해지지 않으면 TDD를 하는 게 거의 불가능하고, 사실 이 둘이 어려우면 일반적인 개발 또는 클린 코드를 작성하는 것 또한 매우 힘들다.

### 단위테스트 vs TDD

* 단위 테스트는 구현에 대한 테스트를 의미한다. TDD는 자동회된 단위 테스트 코드를 먼저 작성함으로써 테스트가 개발을 이끌어가도록 하는 방식

### TDD 예제 ( jest )

* add 함수

```typescript
// 1. 테스트 코드 작성 
// (기본) - 간단한 테스트
test("add", () => {
    expect(add(1, 2)).toBe(3);
});
// (BDD : Behavior Driven Development) 
// Given ( 주어진 상황이나 환경 ) - When ( 행위 ) - Then ( 결과 )
describe("add", () => {
    context("두 개의 파라미터가 주어졌을 때", () => {
        it("두 숫자의 합을 리턴한다", () => {
            // when
            const sum = add(1, 2);
            
            // then
            expect(sum).toBe(3);
        });
    })
});

// 2. add 함수 작성
const add = (a: number, b: number) => a + b;

// 3. 확장
describe("add", () => {
    context("파라미터가 없을 때", () => {
        it("0을 리턴한다", () => {
            expect(add()).toBe(0);
        });
    })
    
    context("두 개의 파라미터가 주어졌을 때", () => {
        it("두 숫자의 합을 리턴한다", () => {
            expect(add(1, 2)).toBe(3);
        });
    })
    
    context("세 개의 파라미터가 주어졌을 때", () => {
        it("세 숫자의 합을 리턴한다", () => {
            expect(add(1, 2, 3)).toBe(6);
        });
    })
    // ...
    context("열 개의 파라미터가 주어졌을 때", () => {
        it("열개 숫자의 합을 리턴한다", () => {
            expect(add(1, 2, 3, 4, 5, 6, 7, 8, 9, 10)).toBe(55);
        });
    })
});

// 3. add 함수 리팩토링
const add = (...numbers) => {
    if (numbers.length === 0) {
        return 0;
    }
    return numbers.reduce((acc, number) => acc + number, 0);
}
```

### TDD 예제 ( React Testing Library )

* React 컴포넌트를 사용자 입장에 가깝게 테스트 하는 도구

> [https://github.com/testing-library/react-testing-library](https://github.com/testing-library/react-testing-library)\
> [https://github.com/testing-library/jest-dom](https://github.com/testing-library/jest-dom)

```tsx
test("TextField", () => {
    // given
    
    const label = "Name";
    const text = "Tester";
    
    const setText = jest.fn();
    
    beforeEach(() => {
        jest.clearAllMocks();
        // 또는 setText.mockClear();
    })
    
    it("컴포넌트가 렌더링 된다.", () => {
        // when
        render(
            <TextField
                label={label}
                placeholder="Input your name"
                // filterText="Tester"
                text={text}
                // setFilterText={setFilterText}
                setText={setText}
            />
        )
        
        // then 
        screen.getByLabelText(label);
        screen.getByPlaceholderText(/name/);
        screen.getByDisplayValue(text);
    })
    
    // -----
    context("사용자의 이름이 입력되었을 때", () => {
        it("setText 핸들러가 실행된다.", () => {
            render(
                <TextField
                    label={label}
                    placeholder="Input your name"
                    text={text}
                    setText={setText}
                />
            )
        
            // when
            fireEvent.change(screen.getByLabelText(label), {
                target: { value: "New Name" }
            })
            
            // then
            expect(setText).toBeCalledWith("New Name");
        })
    })
})
```
