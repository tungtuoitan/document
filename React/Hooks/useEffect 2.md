# useEffect

useEffect(setup, dependencyArr)

# chức năng

- cho phép thực hiện side effect trong component mà vẫn giữ cho component pure

# hoạt động của useEffect

- khi component được thêm vào DOM , hàm setup sẽ được thực thi:
- sau khi re-render, nếu dependency thay đổi thì:

* 1. thực thi clean up function với value cũ,
* 2. thực thi setup function với value mới (hầu hết là sau khi browser paint)

- sau khi component được move khỏi DOM thì clean up function được thực thi

# thời điểm thực thi hàm setup

> > Triggering

> > Rendering

> > Committing

_RUN setup in useEffect synchronously khi việc show lastest UI là quan trọng (hiếm khi xảy ra)_

> > paint screen (tức browser rendering)

**RUN setup in useEffect asynchronously (most of the time)**

# dependency array

- phải chứa tất cả các [reactive value] có trong setup function,
- react sẽ so sánh các dependency với các giá trị trước đó bằng Objectijs()
- khi không cung cấp dependency array, setup sẽ chạy lại sau mỗi lần render
- khi dependency array [] rỗng, hàm setup chỉ chạy đúng 1 lần

# lưu ý khi dùng:

- khi hàm setup không chứa side effect thì không cần dùng useEffect
- tránh dùng object/function trong dependency

# Các kịch bản phổ biến:

- Connect đến server
- wrapping Effect in custom Hook
- update state bằng setInterval
- loại bỏ object/function trong dependency để tránh re-run nhiều lần
- Reading the latest props and state from an Effect (đang phát triển)
- Control a non-React widget
- ta cần hiển thị content ở client khác với ở server khi dùng SSR (trường hợp hiếm)
- fetch data
