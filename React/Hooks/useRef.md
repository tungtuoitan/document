# useRef

# chức năng

- cho phép ta tham chiếu 1 giá trị không cần thiết cho rendering

# lưu ý khi dùng

- ta có thể biến đổi ref.current
- khi pass vào JSX như 1 thuộc tính ref, thì sẽ nhận về ref của Node đó
- khi thay đổi ref.current, React không re-render component (vì ref là plain object)
- không write/read ref.current trong quá trình rendering, ngoại trừ khi khởi tạo, vì nó sẽ dẫn đến các hành vi bất thường. tức là chỉ nên dùng nó trong effect hoặc event handler
- ref được sử dụng khá ít
- khi ref lưu DOM element, và component unmount thì ref.current sẽ được gán cho null
- khi ref được thêm vào JSX như 1 thuộc tính, điều này sẽ ra lệnh cho React thêm DOM element tương ứng vào ref.current. và ta chỉ có thể thêm ref vào html element trong jsx, chứ k thể truyền vào React component khác (<MyInput ref={inputRef} />) vì React muốn thế
- Ref vẫn tồn tại và k bị reset sau mỗi lần re-render
- React sẽ gắn DOM element vào ref.current ngay sau phase commit,
- thông thường ta sẽ truy cập ref trong event handler
- Ref là escape hatch, (vì React không theo dõi được thao tác DOM của ta khi dùng ref), nên ta chỉ dùng ref khi ta buộc phải "step outside React"
- Tránh thay đổi DOM (vì nó được quản lí bởi React),nếu ta dùng ref để thay đổi DOM thường xuyên, rất dễ xảy ra conflict
<!-- ví dụ minh họa: https://react.dev/learn/manipulating-the-dom-with-refs#best-practices-for-dom-manipulation-with-refs -->

- hầu hết, ref dùng để lưu DOM element
- value của ref là local, chỉ có scope trong 1 component duy nhất

- tránh tạo lại ref's content
<!-- https://react.dev/reference/react/useRef#avoiding-recreating-the-ref-contents -->

- cách tránh null check của typescript khi khởi tạo ref trong những lần re-render
<!-- https://react.dev/reference/react/useRef#avoiding-recreating-the-ref-contents -->

# các kịch bản phổ biến

- referencing a value để lưu timeout IDs,
- lưu data (data này k liên quan gì đến rendering)

- lưu và thao tác với DOM element
  <!-- https://react.dev/learn/manipulating-the-dom-with-refs -->
  -quản lí list ref với ref callback
- dùng với useImperativeHandle để expose API/custom function

# vì sao ta cần dùng ref để thao tác với DOM

- vì các hoạt động manipulate như: focus()/scroll to node/ đo size/position... không có trong react

# cách quản lí 1 list ref

- dùng ref cho parent element và truy cập thủ công vào child, (điểm yếu: code sẽ sai khi DOM thay đổi)
- dùng ref callback

# tương tác với DOM element khi nó chưa được tạo ra

ví dụ:

<!-- https://react.dev/learn/manipulating-the-dom-with-refs#flushing-state-updates-synchronously-with-flush-sync -->

- lí do: vì thứ tự thực thi diễn ra: manipulate() --> update state --> create DOM element. cho nên việc manipulate sẽ diễn ra TRƯỚC KHI element được tạo ra

- giải quyết:
- ép React update state bằng flushSync
-

# troubleshooting

- không lấy ref được ( do ta k thể dùng ref trong component, ví dụ cách dùng sai: <MyInput ref={inputRef} />)
