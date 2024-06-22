---
description: 타입스크립트
---

# TypeScript

> 타입스크립트 핸드북
>
> [https://www.typescriptlang.org/ko/docs/handbook/intro.html](https://www.typescriptlang.org/ko/docs/handbook/intro.html)

* 간단하게 REPL ( read-eval-print loop ) 을 쓰고 싶다면 ts-node 를 실행

`npx ts-node`

### 타입 지정

```typescript
// 직접 지정
let name: string;
name = "my-name";
name = 123; // error

// Object 의 타입도 지정 가능
let human: {
    name: string;
    age: number;
};

// 타입을 저장해두고 재사용 가능
type Human = {
    name: string;
    age: number;
} 

interface Human {
    name: string;
    age: number;
}

let boy: Human;

const add = (a: number, b: number): number => a + b;
add(1, 2) // 3
add('1', '2') // error

// 정해진 값으로 타입을 지정할 수 있다.
let category: "food";
category = "food";
category = "book"; // error

// 배열
let numbers: number[];
numbers = [1, 2, 3];
numbers = ['1', 2, 3]; // error

// Tuple
let tuple: [number, string];
tuple = [1, '2'];
tuple = [2, 2]; // error

// 타입 추론
let num = 1; // number
let name = "kim" // string

// Union 
type Category = "food" | "book";
let category = "food";
category = "book";
category = "house"; // error

// Optional Parameter
const add = (a: number, b?: number) => a + (b || 0);
add(1) // 1
// 위와 같은 경우 기본값을 넣어 주는 것이 더 좋다.
const add = (a: number, b: number = 0) => a + b;

// Intersection Type
type Human = {
    name: string;
    age: number;
}

type Creature = {
    hp: number;
    mp: number;
}

type Person = Human & Creature;
let person: Person;
person = { name: "kim", age: 13 } // error

// Generics
type Type<T> = T;
let test: Type<string>;
test = "1";
test = 1; // error

```

* [타입 별칭과 인터페이스의 차이점 ](https://www.typescriptlang.org/ko/docs/handbook/2/everyday-types.html#%ED%83%80%EC%9E%85-%EB%B3%84%EC%B9%AD%EA%B3%BC-%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4%EC%9D%98-%EC%B0%A8%EC%9D%B4%EC%A0%90)
  * 타입은 새로운 프로퍼티를 추가하도록 개방
  * 인터페이스는 항상 확장될 수 있다.

### vscode 자동완성

* 오래된 라이브러리의 경우 `d.ts` 파일만 제공해준다. ( `@types/~~` )
* 해당 파일을 제공하면 vscode 에서 자동완성과 실시간 오류검사 기능을 사용할 수 있다.

### 참조

* [Utility Type](https://www.typescriptlang.org/docs/handbook/utility-types.html)
* [더 좋은 타입스크립트 프로그래머로 만드는 11가지 팁](https://megaptera.notion.site/11-33889c962a514a9a814be0d6bb3325ca)
