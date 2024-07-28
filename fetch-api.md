---
description: 브라우저에서 제공하는 네트워크 요청에 관련된 API
---

# Fetch API

> Fetch API mdn 문서
>
> [https://developer.mozilla.org/ko/docs/Web/API/Fetch\_API](https://developer.mozilla.org/ko/docs/Web/API/Fetch\_API)

### Fetch API 사용 예제

* 기본적인 사용법

```typescript
const getProducts = async () => {
    const response = await fetch("http://localhost:3000/products");
    const reader = response.body.getReader();

    const chunk = await reader.read();
    const body = new TextDecoder().decode(chunk.value);
    
    const data = JSON.parse(body);
    return data;
}

getProducts();
```

* json 메서드를 활용한 방법
  * 이전 사용 방법보다 훨씬 간결하게 사용할 수 있다.

```typescript
const getProducts = async () => {
    const response = await fetch("http://localhost:3000/products");
    const data = await response.json();
    return data
}

getProducts();
```

* 다양한 HTTP 메서드 사용 가능

```typescript
// GET (생략 가능)
const response = await fetch(url, {
    method: "GET"
});

// POST
const response = await fetch(url, {
    method: "POST"
});

// DELETE
const response = await fetch(url, {
    method: "DELETE"
});

// PATCH
const response = await fetch(url, {
    method: "PATCH"
});

// PUT
const response = await fetch(url, {
    method: "PUT"
});
```
