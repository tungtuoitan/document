# TỔNG QUAN

- biến luôn luôn liên kết với ô nhớ trong stack
- ô nhớ stack có 2 loại: primitive value / địa chỉ ô nhớ Heap
- reference value luôn được lưu trong ô nhớ Heap

# NGUỒN GỐC SỰ KHÁC BIỆT

- Primitive value có kích thước không đổi, nên value được lưu vào stack
- Reference value có kích thước thay đổi(NOT fixed size), nên chúng được lưu vào Heap, ô nhớ Stack sẽ lưu địa chỉ của ô nhớ Heap

# HỆ QUẢ
## Primitive
- khi gán A cho B, và thay đổi B thì A không bị ảnh hưởng
## Reference
- khi biến đổi value A, thì value B cũng thay đổi theo, (vì cả A và B cùng trỏ đến 1 reference value)

## source

https://www.freecodecamp.org/news/primitive-vs-reference-data-types-in-javascript/
