# side effect

- là những hoạt động trong 1 hàm, nhưng có làm thay đổi something nằm bên ngoài scope của hàm đó

- ví dụ:
- hoạt động thay đổi input của hàm đó
- call API (vì khi all API)
- console.log()
- fetch đến server (vì nó sẽ thêm 1 entry vào log file)
<!-- SOURCE:  https://daveceddia.com/react-redux-immutability-guide/#what-is-immutability -->

## hiệu ứng "side effect" của 1 hàm

- 1 hàm được gọi là có "side effect" khi có các hoạt động như:
- thay đổi/ đọc biến non-local
- biến đổi tham số
- "tạo ra" lỗi/exception
  thực hiện I/O
- gọi các hàm có side effect

# "render"

- là việc thực thi code và trả về JSX

# Wiget

- là 1 UI element dùng để hiển thị thông tin, hoặc làm công cụ để tương tác với OS hoặc 1 app

# Kĩ thuật Memoization

- là kĩ thuật tối ưu hóa performance bằng cách cache lại kết quả của các logic tính toán phức tạp

# hoạt động "lên lịch"/schedule

- là thực hiện 1 hành động trong tương lai, sau 1 khoảng thời gian cho trước

# "lag behind"

# reactive value

- reactive value có thể là: prop, state, và các biến và các hàm được khai báo trực tiếp trong component

# best practice ??

# escape hatch

# snapshot

# error prone

# expose

- xuất biến/type ra ??

# shallow comparison / so sánh nông

- là so sánh địa chỉ của chúng
- vd: Object.is() là phép so sánh nông

# refactor

- là việc tái cấu trúc code mà không làm ảnh hưởng đến chức năng
