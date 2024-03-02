# npm run serve
chuẩn bị dependence (kiểm tra + tải về)
biên dịch các .vue thành các file tĩnh
khởi động vue local server

## vue-cli-service
- là file js trong dự án vue, cho phép ta xem và kiểm tra app trong quá trình phát triển

## serve
- là option trong câu lệnh
- dùng để khởi chạy local development server

# mô hình declarative
- là mô hình lập trình mà, khi xây dựng cấu trúc và element của chương trình, dev chỉ thể hiện logic mà k thể hiện luồng điều khiển ????

# vue local server
## chức năng:
- phục vụ file tĩnh  khi trình duyệt fetch đến, các file tĩnh này được biên dịch từ các file component
- live reloading: tự động reload website khi sourcecode thay đổi

# Progressive framework
- là framework cho phép dev phát triển ứng dụng dần dần (tiến tới), cho phép mở rộng (thay vì phát triển 1 ứng dụng hoàn chỉnh từ đầu)
- progressive có nghĩa là tiến tới
# cli
- là phần mềm
có chức năng nhận vào input để thực thi các chức năng OS

# vue cli
## chức năng:
- tạo project nhanh chóng
- quản lí dependency
- chạy app trong môi trường local
- biên dịch sourcecode thành file tĩnh
đóng gói ứng dụng
- mở rộng và tùy chỉnh quy trình phát triển ????
- tự động biên dịch và đóng gói ứng dụng để có thể dùng locally (trong môi trường phát triển)

# build step

là bước biên dịch + tối ưu + đóng gói, chỉ dùng khi triển khai ứng dụng

# app instance

- là đối tượng đại diện của app
- sử dùng Model view view model pattern (MVVM)
- chấp nhận options object
- cách tạo: new Vue() // createApp().mounted
- điều khiển toàn bộ hoạt động của ứng dụng (khởi tạo + quản lí…)

# đối tượng cấu hình

- là đối tượng truyền vào new Vue // createApp

## bao gồm:

- el: chỉ định HTML element mà app instance sẽ gắn vào
- data: cung cấp data cho app
- method: chứa phương thức của app
- computed: chứa các thuộc tính tính toán

# setup()

- là phương thức đặc biệt
- dùng để cấu hình và khởi tạo component
- trả về đối tượng chứa: hàm / biến / đối tượng ref để dùng trong template

# đăng kí component

- là thông báo cho Vue biết là ta đã tạo 1 component mới và muốn sử dụng nó
- cần đăng kí component vì để Vue biết dc vị trí nó

# global component

là component khả dụng trên toàn app, có thể dùng ở mọi template ???

# SFC / single file component

là 1 loại file đặc biệt, để chứa toàn bộ code liên quan đến 1 component
.vue

# npm create vue@latest

- tải và thực thi create-vue

## create-vue

- là công cụ dàn giáo chính thức của Vue

# IN-DOM template
- ?????????

# composition funciton

- là hàm lớn, được tạo ra từ các hàm nhỏ hơn ?????

# watch()
## chức năng:
- thực hiện các hoạt động side-effect, tương tự useEffect

# defineProp 
- là hàm dùng để nhận input từ parent

# vite
- là built tool giúp xây dựng fe nhanh và hiệu suất

# emit
- là hàm kích hoạt sự kiện custom, và các component khác lắng nge

# reactive()
- tạo state, và Vue có thể theo dõi các state này
