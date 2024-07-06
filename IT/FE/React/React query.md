# Chức năng của react query
- dùng để quản lí data trên máy khách khi website dùng cơ chế *SSR*
-

# Tại sao không dùng state management library mà lại dùn react query ?

- vì state management lib không tương thích tốt với asynchronous/ server state

# sự khác biệt giữa client state và server state ?

- client state:

* được lưu trong app
* dùng hàm đồng bộ để truy cập/update state

- server state

* được lưu remotely??
* dùng asynchronous func để truy cập (fetch) / update state
