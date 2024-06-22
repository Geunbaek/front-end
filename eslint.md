---
description: 정적 프로그램 분석 도구
---

# ESLint

> ESLint 공식문서
>
> [https://eslint.org/](https://eslint.org/)

### 사용하는 이유?

* 코드 스타일 통일
* 잠재적인 문제 발견에 도움
* 최신 트렌드를 학습하는 데에 도움을 준다.

### VSCode 확장

* [https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
* vscode 에서 저장을 할 때마다 `lint --fix` 를 실행한 것과 동일한 동작을 한다.

```json
// .vscode/settings.json
{
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  }
}
```
