# useMemo()

- chức năng: lưu lại kết quả tính toán của 1 tập hợp dependency cụ thể và tái sử dụng kq khi dependency không thay đổi

## lưu ý khi dùng

- nên là last resort option

## các kịch bản phổ biến

### dùng để bỏ qua tính toán phức tạp

### dùng với memo() để bỏ qua re-render không cần thiết của child component

import { memo } from 'react';
const List = **memo**(function List({ items }) {
// ...
});

---

export default function TodoList({ todos, tab, theme }) {
// Tell React to cache your calculation between re-renders...
const visibleTodos = **useMemo**(
() => filterTodos(todos, tab),
[todos, tab] // ...so as long as these dependencies don't change...
);
return (

<div className={theme}>
{/_ ...List will receive the same props and can skip re-rendering _/}
<List items={visibleTodos} />
</div>
);
}

## Troubleshooting

### tính toán chạy 2 lần khi re-render

https://react.dev/reference/react/useMemo#my-calculation-runs-twice-on-every-re-render

### useMemo() trả về undefinded, nhưng expect là object

https://react.dev/reference/react/useMemo#my-usememo-call-is-supposed-to-return-an-object-but-returns-undefined

### re-calculation mỗi khi re-render

https://react.dev/reference/react/useMemo#every-time-my-component-renders-the-calculation-in-usememo-re-runs

### cần dùng useMemo trong mỗi item trong loop nhưng không được phép

https://react.dev/reference/react/useMemo#i-need-to-call-usememo-for-each-list-item-in-a-loop-but-its-not-allowed
