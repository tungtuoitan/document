# useContext()

- giúp ta đọc context từ component bên trên

## Context

- hiểu đơn giản là tập hợp các biến, value của 1 hàm (mà cụ thể ở đây là function component)

## return value

- trả về value của SomeContext.Provider gần nhất, nếu không có Provider nào thì trả về defaultValue đã khai báo trong createContext
- return Value của useContext luôn up-to-date. và React luôn re-render khi returnValue thay đổi

## Các kịch bản phổ biến khi dùng context

- truyền data xuống sâu
- update state: bằng cách truyền value dạng: {state, setState}
- viết đè lên context đã có, vì useContext sẽ chỉ lấy value của context "gần" nhất
- tối ưu performance khi truyền đi object/function: <!-- https://react.dev/reference/react/useContext#optimizing-re-renders-when-passing-objects-and-functions  -->

## lưu ý khi dùng

- useContext chỉ nhận value từ Provider của Component bên trên, tức useContext của component A không nhận value từ Provider của A

- việc skip re-render của memo() không ảnh hưởng đến việc component nhận các value up-to-date
- Khi value của context thay đổi,React sẽ re-render các component dùng value đó re-render,
- có thể dùng default value trong createContext(), để tránh bug khi thiếu Provider và hoạt động tốt ở Test Enviroment
- trong 1 số trường hợp, quá trình build sẽ tạo ra 2 module trùng lặp, điều này làm cho 2 đối tượng Context không === nhau, dẫn đến việc Context không hoạt động (vì context chỉ hoạt động khi SomeContext cung cấp value và SomeContext nhận value === nhau)
- khi có nhiều Provider và ta muốn code gọn gàng, ta có thể gộp chúng lại và tạo thành Provider component:
<!-- https://react.dev/reference/react/useContext#extracting-providers-to-a-component -->

## Troubleshooting

- không nhận được value từ Provider
<!-- https://react.dev/reference/react/useContext#my-component-doesnt-see-the-value-from-my-provider -->
- luôn nhận undefine value mặc dù có dùng defaultValue
<!-- https://react.dev/reference/react/useContext#i-am-always-getting-undefined-from-my-context-although-the-default-value-is-different -->
