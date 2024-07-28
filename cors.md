---
description: 교차 출처 리소스 공유
---

# CORS

> CORS ( Cross-Origin Resource Sharing )
>
> [https://developer.mozilla.org/ko/docs/Web/HTTP/CORS](https://developer.mozilla.org/ko/docs/Web/HTTP/CORS)
>
> SOP ( Same-Origin Policy )
>
> [https://developer.mozilla.org/ko/docs/Web/Security/Same-origin\_policy](https://developer.mozilla.org/ko/docs/Web/Security/Same-origin\_policy)

### CORS 란

* 웹 브라우저는 Same Origin Policy에 따라 웹 페이지와 리소스를 요청한 곳(여기서는 REST API 서버)이 서로 다른 출처(포트까지 포함)일 때 서버에서 얻은 결과를 사용할 수 없게 막는다.&#x20;
* 서버에 요청하고 응답을 받아오는 것까지는 이미 완료된 상황에서 브라우저가 차단 하는 현상
* 프로토콜, 호스트 그리고 포트까지 모두 일치하여야 동일 출처
* 예시 : http://store.company.com
  * 프로토콜 : https://
  * 호스트 : store.company.com
  * 포트: 80, 8080 ( http의 경우 80, 8080 / https의 경우 443 )

### 해결방법

* REST API 서버에서 Headers에 “Access-Control-Allow-Origin” 속성을 추가하면 된다.
* 로컬 환경에서는 React의 경우 proxy 설정을 통해 임시로 해결이 가능하다.
