# lazy()

const SomeComponent = lazy(load)

# chức năng

- cho phép ta trì hoãn load component code cho đến khi nó được re-render

# thành phần

## tham số: hàm load().........

- là hàm, trả về Promise hoặc [thenable]
- React sẽ chỉ call load() khi ta muốn render [returned component]
- khi call load(), nó sẽ render <resolved value’s .default> như 1 react component
- returned Promise và Promise resolbed value sẽ được cached

## returned component

- là component mà ta muốn render
  const MarkdownPreview = lazy(() => import('./MarkdownPreview.js'));
- trong ví dụ này, returned component là MarkdownPreview

- khi code của lazy component đang loading, nếu cố render returned component thì nó sẽ Suspense, do đó ta có thể dùng <Suspense> ở đây

### thenable

- là Promise-like object với then method

# các kịch bản phổ biến
- lazy-loading với suspense

# troubleshooting
- lazy component state bị reset 1 cách bất ngờ
<!-- https://react.dev/reference/react/lazy#my-lazy-components-state-gets-reset-unexpectedly -->