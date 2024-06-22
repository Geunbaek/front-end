---
description: 특별한 설정 없이 바로 사용 가능한 빌드도구
---

# Parcel

> parcel 공식문서
>
> [https://parceljs.org/](https://parceljs.org/)

* 번들링
  * 여러개의 파일들을 하나로 합쳐주는 작업

### 설정

```json
// package.json

{
    "source": "./index.html",
}
```

* 정적파일 처리
  * [parcel-reporter-static-files-copy](https://github.com/elwin013/parcel-reporter-static-files-copy)

```json
// .parcelrc

{
  "extends": ["@parcel/config-default"],
  "reporters":  ["...", "parcel-reporter-static-files-copy"]
}
```

### 배포

```
npx parcel build
npx servor ./dist
```
