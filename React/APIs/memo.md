# memo

const MemoizedComponent = memo(SomeComponent, arePropsEqual?)

# chức năng

- cho phép bỏ qua re-render 1 component khi props không thay đổi

# lí do memo() tồn tại ?

- để tối ưu hiệu suất bằng cách khắc chế việc re-render do parent re-render

# arePropsEqual

- dùng để so sánh 2 props xem có === nhau hay không theo cách của mình, thay vì cách so sánh mặc định của React (Object.is),
- hàm này tồn tại vì ta muốn performance tốt hơn, do đôi lúc cách so sánh mặc định (Object.is()) là tốn kém không cần thiết
- hàm nên trả về true nếu preProps === newProps, false nếu không =
- hàm này nhận vào 2 tham số , preProps và newProps,
- thông thường ta k cần dùng tham số này
- khi dùng arePropsEqual, nhớ đo lại performance để kiểm tra xem: việc dùng arePropsEqual có cải thiện hiệu suất không?
- khi so sánh thì phải so sánh toàn bộ props

# lưu ý khi dùng:

- hầu hết thì component sẽ k re-render khi prop k thay đổi, nhưng điều này không chắc chắn 100%, vì đôi khi React cũng re-render lại để tối ưu hóa
- khi dùng với memo, component vẫn re-render khi state bên trong hoặc context hay đổi
- khi đo lường performance, hãy chắc chắn React đang chạy trong production mode
- để hạn chế re-render, hãy truyền minimum props xuống child
<!-- ví dụ: function GroupsLanding({ person }) {
  const hasGroups = person.groups !== null;
  return <CallToAction hasGroups={hasGroups} />;
}

const CallToAction = memo(function CallToAction({ hasGroups }) {
// ...
}); -->

# các kịch bản phổ biến:

- bỏ qua re-render khi prop k đổi, để khắc chế việc re-render do parent re-render

# ta có nên dùng memo() ở mọi nơi không ?

# khi nào nên dùng memo ?

- khi component re-render nhiều lần, với cùng 1 props và việc re-render là expensive
- khi performance không bị lag, thì không nên dùng memo
- memo vô dụng với comoponent có prop thay đổi liên tục
- việc dùng memo chỉ có giá trị
