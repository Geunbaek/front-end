---
description: End-To-End Test
---

# E2E Test

> 종단 간 테스트로 사용자의 입장에서 사용하는 상황 (시나리오) 를 가정하고 테스트 하는것 ( 모킹 데이터가 아닌 실제 api 사용 )

### Playwright

> [https://playwright.dev/](https://playwright.dev/)

* 웹 브라우저 기반 E2E 테스트 자동화 도구.
* Headless Chrome을 기반으로 한 Puppeteer를 계승하면서, 더 많은 웹 브라우저를 지원한다.
* playwright.config.ts&#x20;
  * [https://playwright.dev/docs/test-configuration](https://playwright.dev/docs/test-configuration)

### codeceptjs

> [https://codecept.io/](https://codecept.io/)

* 인간 친화적인 E2E 테스팅 도구

```bash
# 설치
npx codeceptjs init

# 웹 브라우저를 화면에 띄워 테스트를 실행합니다.
npm run codeceptjs

# 웹 브라우저를 화면에 띄우지 않고 테스트를 실행합니다.
npm run codeceptjs:headless

# 웹 브라우저에 CodeceptUI를 띄워 훨씬 편학게 테스트를 실행합니다.
npm run codeceptjs:ui
```

* 예제

```typescript
Feature('Google');

Scenario('Search “CodeceptJS”', ({ I }) => {
  I.amOnPage('<https://www.google.com/ncr>');
  I.fillField('[name="q"]', 'CodeceptJS');
  I.click('Google Search');
  I.see('codecept.io');
});
```

* E2E 테스트를 조금 더 인간친화적으로 작성할 수 있다.
* 개발자가 아닌 사람이라도 검토가 가능할 정도로 문법이 명확하고 간결하다.
