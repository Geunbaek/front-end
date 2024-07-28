---
description: Nodejs 를 위한 빠르고 개방적인 간결한 웹 프레임워크
---

# Express

### 왜 Express인가 ?

* express 는 프레임워크로 웹 애플리케이션을 만들기 위한 각종 라이브러리와 미들웨어를 포함하고 있어 개발에 편의성을 제공
* 개발자에게 일정한 코드 규칙을 강제하여 일관성 있는 코드규칙과 구조의 통일성을 줄 수 있다.

### express 예제

1. express 설치

```bash
mkdir express-app
cd mkdir express-app

touch .gitignore
echo "/node_modules/" > .gitignore

npm init -y

# 타입스크립트 설치 및 설정
npm i -D typescript
npx tsc --init

# eslint 설치 및 설정
npm i -D eslint
npx eslint --init

# ts 파일을 실행할 ts-node 설치
npm i -D ts-node

npm i express
# ts를 사용하는 경우 설치
npm i -D @types/express
```

2. hello world 예제

```typescript
// app.ts
import express from "express";

const port = 3000;
const app = express();

app.get("/", (req, res) => {
    res.send("Hello world!");
})

app.listen(port, () => {
    console.log(`Server listening at http://localhost:${port}`);
})
```

3. 실행

```bash
npx ts-node app.ts
```

