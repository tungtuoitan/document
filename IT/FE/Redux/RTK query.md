# **RTK Query**

## các bước dùng redux query

- tạo api (viết endpoint)
<!-- dùng createAPI -->

(auto render ra hook từ endpoint)

- set RTK Query làm middleware trong RTK

- xuất api và useApiQuery

- dùng api
<!-- tức: lấy data từ api -->

## chức năng

- dùng để fetch data và cache
- update data

## thành phần

### createApi()

- createApi(api, options)
- gọi buildCreateApi()

### api

- là đối tượng chứa các endpoint

## Module

- là method của RTK Query,
- quyết định cách createAPI xử lí Endpoint

- [module](./module.md)

## khi nào nên dùng RTK Query

- đã có react redux app, và muốn đơn giản hóa logic fetch data
- muốn dùng Redux DevTool để xem lịch sử thay đổi của state
- muốn tích hợp RTK Query với hệ sinh thái Redux
- khi logic cần hoạt động bên ngoài React

## định nghĩa

- là 1 phần của thư viện rtk

## source

<!-- https://redux-toolkit.js.org/rtk-query/usage/queries -->

# **Mutation**

## chức năng

- gửi updated data đến server
- áp dụng thay đổi vào data trong local cache
- ép re-fetch
- loại bỏ data ra khỏi local cache

# **Another**

## local cache

