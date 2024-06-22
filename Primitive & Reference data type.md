
# TỔNG QUAN
- primitive value có kích thước không đổi, nên js lưu chúng vào call stack(execution context)
- khi ta truy cập value của 1 biến, ta trực tiếp thao tác với value trong biến đó, có nghĩa: khi copy A.value cho B, thì B sẽ nhận được 1 bản copy của A.value
- mỗi 1 primitive data được tạo ra, thì nó sẽ được thêm vào stack


# khi gán value cho 1 biến
- khi gán value cho 1 biến, tên biến trỏ đến new box, và trong box chứa value
# khi re-assign
- khi re-assign, tên biến trỏ đến new box khác, và trong box chứa new value

# khi mutate bên trong biến
- tên biến vẫn trỏ đến current box, nhưng value bên trong bị thay đổi

# cách thức === hoạt động với array, object
- so sánh địa chỉ của box

[](https://stackoverflow.com/questions/122102/what-is-the-most-efficient-way-to-deep-clone-an-object-in-javascript)



# khi tạo ra 1 biến
- thì biến đó sẽ được liên kết với 1 ô nhớ tương ứng

# 2 loại value
## Pass by Value
- khi gán biến a cho biến b, js sẽ copy a.value, bỏ vào ô nhớ của b
- khi đó, ô nhớ của a và b không liên quan đến nhau, và value bên trong 2 ô nhớ bằng nhau, nhưng cũng không liên quan đến nhau 

# tham chiếu/reference là gì?
- là giá trị 


# ANOTHER
## Stack
- là 1 cấu trúc dữ liệu, dùng để lưu trữ/truy cập data 1 cách nhanh chóng


