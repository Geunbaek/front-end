---
description: front-end 개발 환경 세팅
---

# 개발 환경 세팅

## Node 개발 환경 세팅

* fnm ( Fast Node Manager )&#x20;
  * Nodejs 버전 관리 도구
  *    nvm 에 비해 빠른 속도 ( Rust 로 작성되어 있음 )
  * 설치와 구성이 nvm 에 비해 쉬움
* LTS ( Long Term Support )
  * 안정적인 버전
  * 꼭 최신버전을 따라갈 필요는 없다.

## Typescript + React + Jest + Parcel 개발 환경 세팅

```sh
mkdir my-app
cd my-app

code .

npm init -y
touch .gitignore # gitignore.io 또는 https://github.com/github/gitignore 참고

npm i -D typescript # typescript 설치
npx tsc --init # tsconfig.json 파일 생성 ( jsx 속성 값 변경 "react-jsx" )

npm i -D eslint # eslint 설치
npx eslint --init # jest 사용을 위해 env 에 jest: true 를 추가해준다.
touch .eslintignore # eslint 예외 파일 설정

# react 설치
npm i react react-dom
npm i -D @types/react @types/react-dom

# jest 설치
npm i -D jest @types/jest @swc/core @swc/jest \
    jest-environment-jsdom \
    @testing-library/react @testing-library/jest-dom@5.16.4
touch jest.config.js 

npm i -D parcel
```

