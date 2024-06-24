# Rule của React (dùng để viết code dễ đọc và chất lượng)

- pure component
- Return value của Hook | arg truyền vào Hook | value sau khi truyền vào JSX phải Immutable
- Không được gọi component function trực tiếp, (đó là việc của React)
- Chỉ được dùng Hook 1 bằng cách: gọi Hook trong component/Hook và ở top-level

# "React" package

## chức năng:

- cung cấp công cụ để viết React code

## Hook

7 loại hook:

- State Hook
- Context Hook
- Ref Hook
- Effect Hook
- Performance Hook
- Other Hook
- Custom Hook

## Built-in Components

- <Fragment>
- <Profiler>
- <Suspense>
- <StrictMode>

## APIs......

6 Built-in APIs:

### createContext()

### forwardRef()

### lazy()

### memo()

- lợi ích: tối ưu performance
- hoạt động: lưu lại return value cùng props cụ thể của 1 component để tái sử dụng
- Tái sử dụng: khi re-render 1 component, React sẽ so sánh nông current props và cached props, nếu bằng nhau thì sẽ tái sử dụng

#### Khi nào nên dùng:

- logic phức tạp (expensive)
- props giống nhau xảy ra thường xuyên
- bị ép re-render bởi parent
- kích thước component vừa hoặc lớn

#### tại sao k dùng cho mọi component ?

- nó có tradeoff
- dùng sai sẽ tốn bộ nhớ, mà k optimize được chút nào
- không phải component nào cũng cần

#### lưu ý:

- khi props thay đổi thường xuyên, thì memo() k mang lại lợi ích rõ rệt

#### tradeoff

- khó debug hơn, vì memo() sẽ giấu bug trong trường hợp: bug chỉ lòi ra khi props thay đổi
- code khó hiểu hơn
- khó thêm feature trong tương lai

#### Best Practice

- Dùng thêm useMemo/useCallback để tránh trường hợp:
  parent re-render --> props phức tạp "change" --> memo component re-render
  <!-- (https://medium.com/picus-security-engineering/optimization-with-react-memo-7e0b0ffb7536) -->

#### khi component được cached, nhưng state bên trong thay đổi thì component có re-render không?

#### chi phí re-render bao nhiêu là đắt (expensive) ?

### startTransition()

### act()

1 Resource API: use() (chưa phổ biến, chỉ có ở React 19)
## Quá trình update UI
## Directives

- "use client"
- "use server"

# React DOM package

## chức năng:

- cung cấp công cụ để tương tác với DOM
- chỉ được dùng cho web app chạy trên browser

## Hook (k phổ biến)

- useFormStatus (k phổ biến, chỉ có ở React 19)

## React DOM Component (chưa phổ biến)

- chức năng: là công cụ để hỗ trợ built-in HTML / SVG component

### API (hiếm khi dùng)

- createPortal
- flushSync

### Resouce preload API (chưa phổ biến)

- prefetchDNS
- preconnect
- preload
- preloadModule
- preinit
- preinitModule

### Entry Point (k phổ biến)

- react-dom/client
- react-dom/server

### (sắp bị bỏ đi)

- findDOMNode
- hydrate
  -render
- unmountComponentAtNode

## Legacy APIs (k phổ biến)

# Nguyên tắc viết optimize performance code........

- khi child nằm trong parent 1 cách trực quan, nên dùng [](#passing-jsx-as-children) để tránh re-render bởi parent
- ưu tiên dùng local state (đặc biệt là các trạng thái tạm thời(vd: value của input)) , và không dùng [](#lift-state-up) khi k cần thiết
- pure component
- tránh các Effect gây ra update state, tức chỉ dùng Effect cho các hoạt động external
- cố bỏ các dependence không cần thiết trong useEffect

# ANOTHER

## JSX Node

- đây là 1 JSX Node: <List items={visibleTodos} />
- tương ứng với object: { type: List, props: { items: visibleTodos } }
- JSX node có tính immutable
- khi React thấy JSX node === previous JSX node, thì React sẽ bỏ qua k re-render

## như thế nào là expensive calculation ?

- loop qua 1000 object trở lên
- hoặc thời gian tính toán lớn hơn 1ms (dùng console.time để đo)

## làm sao để kiểm tra độ hiệu quả của các kĩ thuật tối ưu performance ?

- dùng console.time

## cách tìm ra các component cần cache

- dùng Profiler

## React theo góc nhìn Javascript

- Xcomponent là 1 function
- console.log(Xcomponent) sẽ trả về hàm Xcomponent
- console.log(<Xcomponent>) === console.log(Xcomponent()) và cùng trả về jsx tương ứng

## JSX là gì trong js ?

- là 1 đối tượng js

  ví dụ:
  const this = <div>xxx</div>
  this =
  {
  "type": "div",
  "key": null,
  "ref": null,
  "props": {
  "children": "x"
  },
  "\_owner": null,
  "\_store": {}
  }

## khi nào component re-render?

- state thay đổi bằng setState
- props thay đổi
- parent re-render

## điều kiện để component re-render khi tahy đổi state

## Tại sao parent re-render thì child re-render?

- vì parent re-render, tức là thực thi lại hàm parent, thì child function cũng được thực thi lại

### khi parent re-render thì props sẽ thay đổi, vậy có re-render 2 lần không ?

## cách tối ưu performance

- dùng component "nặng" làm child props, để tránh re-render bởi [parent re-render]
<!-- const SomeOutsideComponent = () => {
  return (
    <MovingComponent>
      <ChildComponent />
    </MovingComponent>
  );
}; -->
- dùng extends React.PureComponent thay vì React.Component

## Các lí do gây ra performance problem phổ biến

- dùng Effect, và nó tạo ra chuỗi re-render liên tục

# Các kĩ thuật để tối ưu performance

- lazyload img
- list visualization/windowing
- memoization
- throttling and debounce
- code splitting
- react fragment
- web worker
- useTransition hook
<!-- https://www.freecodecamp.org/news/react-performance-optimization-techniques/#list-visualization -->

# CASE PHỨC TẠP

- khi state trong memo component thay đổi, thì có re-render không: CÓ

# CONCEPT

## Effect

- là lối thoát khỏi mô hình React
- giúp ta "bước ra khỏi React, và "đồng bộ" React component với các hệ thống bên ngoài (browser DOM, network,...)

## lift state up

- là đẩy state từ component hiện tại lên component parent

## kĩ thuật shallow comparison

- chức năng: để quyết định xem có re-render 1 component cụ thể không
- hoạt động: React so sánh state, props với các phiên bản state, props trước đó

## Higher Order Component / HOC function

- là 1 hàm nhận vào 1 component làm tham số, và trả về 1 component mới
  [đọc thêm tại] https://www.freecodecamp.org/news/higher-order-components-in-react/

### Chức năng:

- cho phép tái sử dụng logic
- cho phép thêm chức năng vào 1 component đã có

## Passing JSX as children

https://react.dev/learn/passing-props-to-a-component#passing-jsx-as-children

khi viết thế này:
<Parent>
<Child />
</Parent>
--> thì trong Parent, props.children = <Child>

## React element

- là các plain object, cũng là cục JSX trong component

## React Node

## Pure Component

- là phải có các tiêu chí:
- Idempotent
- side effect phải nằm ngoài quá trình render
- Props và State phải immutable
