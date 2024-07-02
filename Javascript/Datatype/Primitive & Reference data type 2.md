# TỔNG QUAN

# PRIMITIVE

## điểm mấu chốt

- primitive value có kích thước không đổi, nên js lưu chúng vào call stack(execution context)

## ví dụ trực quan

- khi khai báo biến A và lưu 50 vào A, computer sẽ tạo ra 1 ô nhớ stack A, và lưu 50 vào đó
- khi khai báo biến B và lưu 50 cho B, computer tiếp tục tạo ra 1 ô nhớ stack B, và lưu 50 vào đó,
- A và B không có 1 chút gì liên quan đến nhau cả
- (hình ảnh)(https://www.freecodecamp.org/news/content/images/size/w1000/2022/01/Purple-Minimal-We-Are-Hiring-Twitter-Post--3-.png)

## Hệ quả

- khi gán A = 100, B vẫn không bị ảnh hưởng

# REFERENCE

# điểm mấu chốt

- Reference value có kích thước thay đổi(not fixed size), nên chúng được lưu vào Heap

## khi gán reference value của biến A cho biến B

- computer sẽ cấp 1 ô nhớ Stack B, và lưu [value ô nhớ Stack A] vào ô nhớ Stack B, và điều này dẫn đến: A và B đều trỏ đến 1 reference value

## Hệ quả

- khi biến đổi refernce value A, thì value B cũng thay đổi theo, (vì cả A và B cùng trỏ đến 1 reference value)

## cách computer đối xử:

- reference value sẽ được lưu trong ô nhớ của Heap
- ô nhớ trong Stack sẽ lưu địa chỉ của ô nhớ Heap
- biến sẽ liên kết với ô nhớ trong Stack

## Ví dụ trực quan

- Khi tạo ra 1 biến và lưu reference data vào biến đó, thì biến không trực tiếp lưu trữ reference value, mà sẽ lưu địa chỉ của ô nhớ heap chứa reference value
  desc img: https://www.freecodecamp.org/news/content/images/size/w1000/2022/01/Purple-Minimal-We-Are-Hiring-Twitter-Post--5-.png

# ANOTHER

## source

https://www.freecodecamp.org/news/primitive-vs-reference-data-types-in-javascript/

## Stack

- là 1 cấu trúc dữ liệu, dùng để lưu trữ/truy cập data 1 cách nhanh chóng

## Heap

- là cấu trúc dữ liệu có dạng cây nhị phân (binary tree-based data structure)
