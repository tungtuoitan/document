# v-text

- update element.textContent
- (textContent chỉ nhận string, mọi thẻ html trong textContent đều hiển thị dưới dạng string)
- nhận vào string
- vd:
  <span v-text="msg"></span>
  <!-- same as -->
  <span>{{msg}}</span>

# v-html

- update innerHTML
- nhận vào string (có nhận thẻ html)
- dễ bị lỗ hổng bảo mật
- scope không apply với content trong v-html

# v-show

- ẩn/hiện element bằng css, dựa vào giá trị truyền vào
- expect: any
- ví dụ: x === true thì one.opacity ===0
    <div class='one' v-show='x'>abcd</div>

# v-if

- chức năng: ẩn/hiện element dựa theo dk
- expect: any
- ví dụ:
- dk ===true thì element tồn tại, dk === false thì element BIến Mất
  <div class='one' v-if='!x'>abcd</div>

- khi v-if element toggle, thì element sẽ bị hủy và xây dựng lại
- có thể dùng trong <template> để toggle cả nhóm phẩn tử bên trong
- kích hoạt transition khi state của v-if thay đổi

- khi dùng cùng nhau, v-if sẽ có độ ưu tiên cao hơn v-for
- vue khuyên ta k nên dùng chúng cùng nhau

# v-else

- chức năng: dự bị cho element v-if / v-else-if
- expect: không có

- có thể dùng trong <template>

# v-else-if

- chức năng: dự bị cho element v-if
- expect: any

- bắt buộc: phải có element v-if / v-else-if đằng trước
- có thể dùng trong <template>

# v-for
- chức năng: render 1 element / 1 khối nhiều lần
- expect: array / object / number / string / iterable / map / Set
- ví dụ: 
<div class="cont" v-for='item in x'>
  <div class='one'>{{ item }}</div>
</div>

- giá trị directive phải dùng alias in expression syntax
- trong alias, ta có thể dùng thêm index của aray, hoặc key của object
- mặc định, v-for sẽ render các item tại chỗ, và k di chuyển chúng, 
- nên dùng key, để vue có thể thay đổi danh sách 1 cách chính xác (tương tự React)

# v-on
- chức năng: lắng nge event x tại element này
- shorthand:@
- expect: function / inline statement / object

# argument
- argument là đối số của event handler
- chỉ nhận vào đối tượng event (e)

## modifiers
- chức năng: bổ sung thuộc tính cho event
- bao gồm:
- .stop:

# v-bind

- cột các thuộc tính/prop với 1 biểu thức/biến
- shorthand: :/.

# v-model

- tạo two-way binding trong các thẻ: <input> / <select> / <textarea>

# v-slot

- ??????????

# v-pre

- bỏ qua biên dịch cho element này và con của nó

# v-once

- render element này 1 lần duy nhất và k update

# v-memo

- ghi nhớ subtree của template
- dùng để optimize performance

- có thể dùng trong các element / component
