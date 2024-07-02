# useImperativeHandle

# chức năng

- dùng để tạo custom ref

# lưu ý khi dùng

- không làm dụng ref, ta chỉ nên dùng ref cho các hành vi như: scroll to a node, focus a node, trigger animation, select text ...
- tức hãy dùng cách khác nếu có thể, vd: đóng mở 1 form bằng cách truyền props Z+ useEffect

# cách kịch bản phổ biến

- expose custom ref cho parent
<!-- https://react.dev/reference/react/useImperativeHandle#exposing-a-custom-ref-handle-to-the-parent-component -->

- expose custom function cho parent
<!-- https://react.dev/reference/react/useImperativeHandle#exposing-a-custom-ref-handle-to-the-parent-component -->
