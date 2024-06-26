# useReducer

const [tasks, dispatch] = useReducer(tasksReducer, initialTasks);

# chức năng

- cho phép thêm reducer vào component

# reducer

- là hàm update state

# tại sao reducer tồn tại ?

- để cho code gọn gàng hơn

# so sánh useState và useReducer
<!-- https://react.dev/learn/extracting-state-logic-into-a-reducer#comparing-usestate-and-usereducer -->

# cách viết reducer tốt
- reducer phải pure
- mỗi action mô tả 1 tương các của user, cho dù nó dẫn đến nhiều thao tác data
<!-- https://react.dev/learn/extracting-state-logic-into-a-reducer#comparing-usestate-and-usereducer -->

# dùng reducer với Immer để viết dễ hơn
<!-- https://react.dev/learn/extracting-state-logic-into-a-reducer#comparing-usestate-and-usereducer -->