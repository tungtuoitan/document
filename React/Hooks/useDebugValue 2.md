## useDebugValue

- chức năng: thêm label vào custom Hook trong React Devtool
- lợi ích: giúp reader dễ hiểu logic hơn

### cách dùng

- không nên dùng cho mọi customHook vì nó làm code khó hiểu
- nên dùng khi tạo thư viện cho người khác dùng, đặc biệt khi logic trong thư viện phức tạp và khó kiểm tra, uesr dùng lib sẽ hiểu lib dễ hơn nhờ vào debugValue
- truyền format function làm đối số thứ 2 để tránh tính toán không cần thiết:
<!-- https://react.dev/reference/react/useDebugValue#deferring-formatting-of-a-debug-value -->
