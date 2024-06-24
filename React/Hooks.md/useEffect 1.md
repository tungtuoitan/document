# useEffect

useEffect(setup, dependencyArr)

# chức năng

- cho phép thực hiện side effect trong component mà vẫn giữ cho component pure

# hoạt động của useEffect

- setup() khi mount
- clean up(value cũ) và setup(value mới) khi re-render + dependency change
- clean up() khi unmount

# thời điểm thực thi

- trong hầu hết trường hợp, hàm setup được thực thi sau khi browser paint

# lưu ý khi dùng:

- khi hàm setup không chứa side effect thì không cần dùng useEffect
- tránh dùng object/function trong dependency
