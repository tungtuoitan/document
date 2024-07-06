# useId

# chức năng

- dùng để tạo ra unique Id, dùng cho input-label, accessible attribute,..

# lưu ý khi dùng:

- không nên dùng để generate key trong list
- khi dùng với server rendering, nếu tree của client và server không match chính xác với nhau, thì useId sẽ match với nhau

# accessibility attribute

- là các thuộc tính giúp cho người khuyết tật tiếp cận thông tin trên web dễ hơn
<!-- https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA -->

## các accessibility attributes phổ biến

- accessibility attribute là
- aria-label
- aria-labelledly
- tab-index
- role
- title
- alt....

# tại sao useId tồn tại?

- khi ta dùng hardcode id cho accessibility trong react, nó không tốt vì việc re-render diễn ra nhất nhiều lần và ta cần unique id, vậy nên ta cần useId

- ví dụ:
<!-- https://react.dev/reference/react/useId -->
- nói cách khác, ta cần dùng useId để tạo ra unique id ngay cả trong các phiên re-render,

# tại sao useId lại tốt hơn increment counter variable ?

<!-- - https://react.dev/reference/react/useId#why-is-useid-better-than-an-incrementing-counter -->

# các kịch bản phổ biến

- dùng để generate id cho accessible attribute
- gerenate id cho cac element liên quan với nhau (vd: input + label)
- chỉ định prefix cho tất cả generated id khi dùng nhiều react app trong 1 page,
- dùng the same id prefix ở client và server
<!-- https://react.dev/reference/react/useId#using-the-same-id-prefix-on-the-client-and-the-server -->
