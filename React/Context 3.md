# Tổng quan

- context có thể truyền đi sâu bao nhiêu cũng được
- các context luôn độc lập với nhau, không liên quan đến nhau
- 1 component có thể dùng nhiều context

# Chức năng

- giúp ta truyền data trực tiếp đến any-level child component từ parent component, thay vì truyền props dài dòng

# cách dùng

- tạo context: createContext()
- cung cấp context: <LevelContext.Provider value={level}>
- dùng context: useContext(LevelContext);

# Khi nào nên dùng context

- khi code bị dài dòng bởi props, kể cả đã dùng [Pass JSX as Children]

# Các trường hợp dùng Context

- tạo Theming
- cung cấp current user cho subtree
- Routing khi tự build router
- quản lí state phức tạp, [dùng reducer với context]

# cung cấp Context, và dùng context trong cùng 1 component

https://react.dev/learn/passing-data-deeply-with-context#using-and-providing-context-from-the-same-component

# Another...

## nhược điểm của passing props

- code trở nên dài dòng khi truyền đi xa

## props drilling situation

- là trường hợp dùng props để truyền state đi quá sâu,

## dùng reducer với context ....
