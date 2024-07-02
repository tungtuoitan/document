# **1.Tổng quan**

## Chức năng

- cho phép viết logic bdb trong action creator

## return function

### chức năng

thực hiện async logic
tạo action
dispatch action

### parameter

- getState
- Dispatch

### return function của action creator

- function này nhận vào dispatch method và getState function
- cho phép:

* dispatch nhiều action
* thực hiện hoạt động bdb
* truy cập state hiện tại

# **2.Another**

## Middleware (trong redux) là gì ?

- là chương trình cho phép ta tương tác với các action trước khi action gặp reducer

## Thunk là gì ?

- là hàm trả về function
