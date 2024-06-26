# forwardRef

const SomeComponent = forwardRef(render)

- nhận vào render function
- nhận vào ref từ parent và chuyển tiếp đến render function
- trả về JSX của render function

## render function

- nhận vào props và ref của parent

## ref

- ref có thể là object hoặc function
- nếu parent k truyền ref , thì ref sẽ là null

# chức năng

- dùng để expose DOM node cho parent (sử dụng với ref)

# chú ý khi dùng

- ta thường ref đến các low-level comoponent như (button, input...) chứ k thường dùng cho các app-level component ??

# các kịch bản phổ biến

- exposing DOM node đến parent

- chuyển ref qua nhiều component
  const FormField = forwardRef(function FormField(props, ref) {

<!-- https://react.dev/reference/react/forwardRef#forwarding-a-ref-through-multiple-components -->

- expose [imperative handle]
<!-- (https://react.dev/reference/react/forwardRef#exposing-an-imperative-handle-instead-of-a-dom-node) -->
