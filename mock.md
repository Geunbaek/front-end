# Mock

> 항상 backend api 가 구현이 되어있는 상태가 아니다.
>
> 효율적인 작업을 위해 데이터를 직접 모킹하고 테스트하는 능력이 필요하다.

### API mock

#### Jest

<pre class="language-typescript"><code class="lang-typescript"><strong>// jest 의 api 모킹 메서드
</strong><strong>jest.mock('./hooks/useFetchProducts', () => () => {});
</strong>// __mocks__ 폴더 사용시 아래와 같이 사용
// jest.mock('./hooks/useFetchProducts');

test('App', () => {
  render(&#x3C;App />);

  screen.getByText('Apple');
});

// __mocks__ > useFetchProducts.ts
const useFetchProducts = jest.fn(() => {});

export default useFetchProducts;
</code></pre>

#### MSW ( Mock Service Worker )

> [https://mswjs.io/docs/getting-started](https://mswjs.io/docs/getting-started)

* 코드 레벨이 아니라 네트워크 레벨에서 가짜 구현. 오프라인 작업 등을 지원하기 위한 서비스

```typescript
// setupTests.js
import { beforeAll, afterEach, afterAll } from 'vitest'
import { server } from './src/mocks/node'

// 모든 테스트 이전
beforeAll(() => server.listen())

// 각각의 테스트가 끝난 후
afterEach(() => server.resetHandlers())

// 모든 테스트 후
afterAll(() => server.close())
```

```typescript
// mock/handler.ts

const BASE_URL = "http://localhost:3000";

const handler = [
  http.get(`${BASE_URL}/products`, ({ params }) => {
    const {id} = params;
    const product = products.find(product => product.id === id);
    return HttpResponse.json({product});
  }),
  http.post(path, ({ request }) => {
    const product = await request.json();
    const products = products.concat(product);
    return HttpResponse.json({products});
  }),
  http.put(path, async ({ request, params }) => {
    const {id} = params;
    const updatedProduct = await request.json();
    const product = products.find(product => product.id === id);
    
    const products = products.map(product => {
      if (product.id !== id) return product;
      return updatedProduct;
    });
    
    return HttpResponse.json({products});
  }).
  http.patch(path, async ({ request, params }) => {
    const {id} = params;
    const updatedProduct = await request.json();
    const product = products.find(product => product.id === id);
    
    const products = products.map(product => {
      if (product.id !== id) return product;
      return {...product, ...updatedProduct};
    });
    
    return HttpResponse.json({products});
  }).
  http.delete('/user/:id', ({ params }) => {
    const { id } = params
    const products = products.filter(product => product.id !== id);
    return HttpResponse.json({products});
  })
]
```

* msw 로 테스트를 하는 것은 결국 가짜 테스트&#x20;
* 진짜 테스트도 진행해야한다 ( E2E 테스트 ) - playwright
