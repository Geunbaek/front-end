# useEffect

> 렌더링 이후에 해야할 일, React 의 외부와 관련된 일을 처리
>
> 외부 시스템과 컴포넌트를 동기화하는 React Hook
>
> [https://ko.react.dev/reference/react/useEffect](https://ko.react.dev/reference/react/useEffect)

### useEffect

> #### `useEffect(setup, dependencies?)`  <a href="#useeffect" id="useeffect"></a>

* setup
  * Effect 의 로직이 포함된 함수
  * 반환 함수를 통해 clean up 함수를 반환할 수 있다.
* dependencies
  * setup 함수의 코드 내부에서 참조되는 모든 반응형 값을이 포함된 배열
  * dependencies 배열을 빈값으로 선언시 컴포넌트가 렌더링 된 후 한번만 실행된다.
  * 아무런 값도 넣지 않을 경우 렌더링 될 때마다 실행된다.

```typescript
function Component() {
    // 리렌더링 될 때마다 실행
    useEffect(() => {})
    
    // 첫 렌러링 후 한번만 실행
    useEffect(() => {}, [])
    
    // 반환 값으로 clean up 함수를 반환
    useEffect(() => {
        const handler = () => {}
        window.addEventListener("event-name", handler)
        return () => {
            window.removeEventListener("event-name", handler)
        }
    }, [])
    return <></>
}
```

### Reference

* [useEffect 완벽가이드](https://overreacted.io/a-complete-guide-to-useeffect/)
