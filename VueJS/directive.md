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
- nên dùng key, để Vue có thể thay đổi list 1 cách chính xác (tương tự React)

# v-on
- chức năng: lắng nge event x tại element này
- shorthand:@
- expect: function / inline statement / object???

- ta có thể để trống giá trị của v-on (tức hanlder / statement)
- ví dụ: lắng nge xong rồi chặn hành vi mặc định @click.prevent,

- khi dùng v-on trên element thông thường, thì nó sẽ chỉ lắng nge các hoạt động thông thường, chứ k lắng nge custom event (emmit)
- v-on sử dụng vơi emmit ???

- khi dùng v-on trên component, thì toàn bộ các element trong component đó đều sẽ lắng nge sự kiện đó

- nếu giá trị v-on là statement, thì nó có thể dùng đối tượng $event, 
- $event tương tự đối tượng event trong handler thông thường
- ví dụ: <div v-on:click="handle('ok', $event)" >

- syntax khi có nhiều event trong 1 element
- <button v-on="{ click: handleClick, mouseover: handleMouseOver }">
- với syntax này, ta k thể dùng modifiers

# v-bind
- chức năng: cột các thuộc tính/prop với 1 biểu thức/biến
- shorthand: 
- :/. (khi dùng modifier)
- khi các biến và thuộc tính có cùng tên, ta có thể để trống ???????

- expect: any (với tham số) | Object (khi k có tham số)
- ví dụ khi k có đối số: <img v-bind="{ src: imageSource, alt: 'Image' }">

- Argument: attrOrProp ???????
- modifiers:
.camel: chuyển kiểu kebab-case của thuộc tính thành Camel-case
.prop: ?????
.attr: ????????

- đối với class và style, Vue có hỗ trợ array, object
- ví dụ: <div :class="{ active: isActive }"></div

- khi cột, Vue sẽ kiểm tra xem attribute đó có property tương ứng không, nếu có thì Vue sẽ dùng property >> vì như vậy nó hiệu suất hơn
- điều này tốt hầu hết trong mọi trường hợp, nhưng trong custom element thì đôi lúc mình cần dùng .prop/.attr để can thiệp cách thức trên, để

# v-model
- chức năng: tạo two-way binding trong các thẻ: <input> / <select> / <textarea> / component
- expect: phụ thuộc vào input element trong form / output của component

- modifiers:
- .lazy: lắng nge change event, thay vì input event (tức khi dùng .lazy thì sau khi nhập data xong và enter thì UI mới cập nhật)
- .number: chuyển đổi chuỗi nhập liệu thành số
(mặc định của v-model là string, tức khi nhập số vào thì nó cũng là string, nên khi dùng .number thì giá trị đó sẽ là number)
- ví dụ: <input v-model.number="age" type="number">
- .trim: trim chuỗi input

# v-slot
- chức năng: chỉ định <slot> mà data sẽ truyền vào  
- ví dụ: 
<slot-comp v-slot:bottomSlot>'Hello!'</slot-comp> 
component: 
<template>
        <slot name="topSlot"></slot>
        <slot name="bottomSlot"></slot>
</template>
code trên tương ứng với:
<slot ></slot>
<slot >Hello</slot>

- shorthand: #
- expect: JS expression

- 


# v-pre

- bỏ qua biên dịch cho element này và con của nó

# v-once

- render element này 1 lần duy nhất và k update

# v-memo

- ghi nhớ subtree của template
- dùng để optimize performance

- có thể dùng trong các element / component
