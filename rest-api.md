---
description: REST( Representational State Transfer ) 아키텍처 스타일의 설계 원칙을 준수하는 API
---

# REST API

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
* 코드 온 디멘드
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
* 자원에 대한 행위 내용 ( Representations ) : HTTP Message Pay Load



