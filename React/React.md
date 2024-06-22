# ANOTHER.
## làm sao để thay đổi state/variable của parent ?
- truyền hàm có chứa logic thay đổi xuống child

# cách tối ưu performance trong React
- dùng extends React.PureComponent thay vì React.Component (khi dùng PureComponent thì child sẽ re-render khi và chỉ khi dùng setState hoặc props thay đổi)
[](https://stackoverflow.com/questions/122102/what-is-the-most-efficient-way-to-deep-clone-an-object-in-javascript)
