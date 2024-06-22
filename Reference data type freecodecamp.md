
# TỔNG QUAN
- primitive value có kích thước không đổi, nên js lưu chúng vào call stack(execution context)
- khi ta truy cập value của 1 biến, ta trực tiếp thao tác với value trong biến đó, có nghĩa: khi copy A.value cho B, thì B sẽ nhận được 1 bản copy của A.value
- mỗi 1 primitive data được tạo ra, thì nó sẽ được thêm vào stack

## Ví dụ trực quan
- khi khai báo biến A và lưu 50 cho biến A, computer sẽ tạo ra 1 ô nhớ cho A, và lưu 50 vào đó
- khi khai báo biến B và lưu 50 cho B, computer tiếp tục tạo ra 1 ô nhớ cho B, và lưu 50 vào đó,
và 2 biến A và B, ô nhớ của chúng và value 50 của chúng không có quan hệ gì với nhau
[ảnh mô tả](https://www.freecodecamp.org/news/content/images/size/w1000/2022/01/Purple-Minimal-We-Are-Hiring-Twitter-Post--3-.png)

- khi gán A = 100, B vẫn không bị ảnh hưởng 


# ANOTHER
## Stack
- là 1 cấu trúc dữ liệu, dùng để lưu trữ/truy cập data 1 cách nhanh chóng

