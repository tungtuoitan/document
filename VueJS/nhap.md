# side effect

- là những hoạt động trong 1 hàm, nhưng có làm thay đổi something nằm bên ngoài scope của hàm đó

- ví dụ:
- hoạt động thay đổi input của hàm đó
- call API (vì khi all API)
- console.log()
- fetch đến server (vì nó sẽ thêm 1 entry vào log file)
  [1](https://daveceddia.com/react-redux-immutability-guide/#what-is-immutability)

# tạo ra copy của 1 array

let a = [1, 2, 3];
let copy1 = [...a];
let copy2 = a.slice();
let copy3 = a.concat();
[1](https://daveceddia.com/react-redux-immutability-guide/#what-is-immutability)

# các phương thức mutate array

push (add an item to the end)
pop (remove an item from the end)
shift (remove an item from the beginning)
unshift (add an item to the beginning)
sort
reverse
splice
[1](https://daveceddia.com/react-redux-immutability-guide/#what-is-immutability)

# pure function
- là hàm thỏa mãn 2 điều kiện:
- cùng 1 input luôn tạo ra cùng 1 output
- không có side effect
https://daveceddia.com/react-redux-immutability-guide/#what-is-immutability


# deep copy / deep clone

# cách tạo ra deep clone
- structuredClone()
- JSON.parse(JSON.stringify(a))

- lodash.cloneDeep
- Ramda.clone   
- jQuery - jQuery.extend(true, { }, oldObject)

 >> dùng spread operator hoặc các phương thức khác rất dễ bị shallow clone 

https://stackoverflow.com/questions/122102/what-is-the-most-efficient-way-to-deep-clone-an-object-in-javascript
