---
description: 로직을 재사용하기 위한 제일 쉬운 방법
---

# Custom Hook

> [https://ko.react.dev/learn/reusing-logic-with-custom-hooks](https://ko.react.dev/learn/reusing-logic-with-custom-hooks)

### 사용법

* use 로 시작하는 Function을 작성해서 필요한 곳에서 호출하면 된다.

```typescript
function useFetchProducts() {
  const [products, setProducts] = useState<Product[]>([]);

  useEffect(() => {
    const fetchProducts = async () => {
      const url = 'http://localhost:3000/products';
      const response = await fetch(url);
      const data = await response.json();
      setProducts(data.products);
    };

    fetchProducts();
  }, []);

  return products;
}
```

### Reference

* [usehooks-ts](https://usehooks-ts.com/)
  * 다양한 커스텀 훅들을 모아둔 라이브러리
