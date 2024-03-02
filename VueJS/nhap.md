
# directive
- là thuộc tính đặc biệt
là short code của các hoạt động thao tác với DOM
- bắt đầu với v-

# hàm ref()
tạo ra 1 đối tượng tham chiếu đến giá trị x >> nhớ đó Vue có thể theo dõi state
x sẽ được lưu trữ trong thamchieu.value

# lifecycle hook
là các hàm đặc biệt, >> vì thời điểm thực thi gắn liền với lifecycle

# binding
- là "gán" các giá trị / thuộc tính của HTML element cho state >> khi state thay đổi thì element sẽ thay đổi theo
- tức liên kết trạng thái của UI và state với nhau

# v-bind
- 
# v-model
thay thế cho event của các thẻ trong form


# v-text chức năng ?
gán state cho textContent

# option API
là các quy tắc và các hàm để viết component
## đặc điểm:
export default 
đều là thuộc tính trong đối tượng option
được khai báo riêng biệt trong đối tượng option
cách viết phức tạp

# ý nghĩa tên option ?

nói đến việc ta có nhiều loại api để dùng cho 1 mục đích,
ví dụ, muốn tạo ra data cho component, ta có thể dùng data() / prop() / computed

# thuộc tính tính toán / computed property
là các thuộc tính được tính toán từ các state

# Các option API cụ thể và chức năng

STATE
data(): tạo reactive state
thuộc tính props: khai báo props
thuộc tính computed: định nghĩa các thuộc tính tính toán
thuộc tính method: định nghĩa các phương thức của component, các phương thức này sẽ được dùng logic của component
thuộc tính watch: khai báo các callback gắn với sự thay đổi của state
thuộc tính emmited: khai báo các custom event và handler
expose: ???
RENDERING
-template: chứa chuỗi html mở rộng
render: tạo DOM bằng JS-like syntax
thẻ slots: cho phép chèn code vào bên trong childComponent
LIFE CYCLE
beforeCreate / create
beforeMount / mounted
beforeUpdate / update
beforeUnMounted / unmounted
errorCaptured
COMPOSITION
provide / inject: truyền data từ parent vào child
mixins: tái sử dụng logic và option bằng cách định nghĩa chúng và áp dụng vào nhiều component
extends: tạo ra component mới có tất cả options của component cũ, và options riêng
MISC
name: đặt tên cho component
component: đăng kí và khai báo các childcomponent
directives: đăng kí custom directive
COMPONENT INSTANCE (đi với this)
$data: truy cập data của component từ methods
$props…

mỗi app cần 1 component để chứa các child component
đối tượng truyền vào createApp là 1 rootComponent
mỗi component đều là 1 đối tượng

1 website có thể dùng nhiều app instance, nhưng không phổ biến
phổ biến nhất là: dùng vue để xây dựng SPA và chỉ dùng 1 app
ngoài ra 1 website còn có thể dùng nhiều framework khác nhau, và dùng vue để xây dựng 1 phần trang web

# các cách viết component

JS module
FSC

# lợi ích và bất lợi của cách viết FSC và JS module

lợi ích của cách viết fsc:
hot reloading
dễ viết dễ đọc
scoped style

# lợi ích của cách viết js module

hỗ trợ một số tính năng mà sfc k hỗ trợ (vd TypeScript)

# dynamic component

là component có nhiều hơn 1 UI, phụ thuộc vào props truyền vào
diễn biến createApp()
tạo app instance
liên kết với HTML element đã cấu hình
điều khiển DOM
theo dõi state và update

# các hoạt động với App

gắn app vào html element / tháo app
tạo component

# tính năng declarative rendering

- là việc code (mô tả) UI bằng html + state mà k trực tiếp thao tác với DOM>> vì có React, Vue làm việc đó rồi
- declarative: Mô tả
- khi dùng JS thuần, thì để UI cập nhật, bắt buộc phải thao tác với DOM

# tính năng reactivity

- là khả năng tự động cập nhật UI khi dữ liệu, trạng thái của ứng dụng thay đổi
- reactivity có nghĩa là phản ứng: khi state thay đổi, React sẽ "phản ứng" với thay đổi đó

# vue là hệ sinh thái, vậy hệ sinh thái là gì ?

# vue bao hàm gần như toàn bộ các tính năng mà FE cần, vậy toàn bộ các tính năng đó là gì?

# vue rất linh hoạt, linh hoạt chỗ nào?

# built tool enable project là gì? built tool là gì ?

là các dự án được xây dựng bởi built tool

# 2 loại api: option style và composition style

option style: là cách tiếp cận truyền thống
composition style: là cách tiếp cận linh hoạt hơn, tập trung vào chức năng, có từ Vue3

# composition API

là 1 phần của vue 3
cú pháp đơn giản

các composition API


# <template>
- mặc định sẽ có display: none

# alias in expression

# modifiers trong 