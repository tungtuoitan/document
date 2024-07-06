# chức năng

-

# vấn đề

## cache invalidation (làm sao xóa cache cho hiệu quả?)

- data để lâu trong cache sẽ bị cũ, thì tần suất update data thế nào là tốt?

# thứ tự các loại "cache", small but fast

- CPU Register
- L1
- L2
- L3
- Main memory
- SSD
- HDD

# Cache eviction stategy

- là chiến thuật xóa cache khi full cache

## các chiến thuật xóa cache phổ biến

- (LRU) Least Recently Used: là các data ít dùng nhất trong khoảng thời gian gần đây
- RR (Random Replacement): là remove data 1 cách ngẫu nhiên

# các loại cached

# các vị trí cache

## browser cache

##

# **Another**

## cache validation

- là việc xác thực data ở trong cache, bằng cách kết nối đến server để check và update data nếu nó bị cũ

## cache invalidation

- là việc xóa data trong cache

# browser cache

- chỉ 1 user được dùng
- có thể lưu trữ các

# chúng ta kiểm soát web cache thế nào ?

- mỗi khi server gửi response, thì sẽ gửi kèm hướng dẫn: có nên lưu data này vào cache không? và bằng cách nào ?

# bên trong header

## expire

- là mốc thời gian mà data cần refresh
- ex: Mon, 13 Mar 2017 12:22:00 GMT
- nếu format sai, data được coi là cũ

## Pragma

- cung cấp instruction cho client (browser) cách thức cache data

## Cache control

- chỉ định thời gian data được cache và cách thức lưu trữ data
- private: data chỉ được cache ở client và k dc cache ở proxy
- public: data có thể cache ở client lẫn proxy,
- no-store: data k được cache
- max-age=x: chỉ định thời gian data sẽ bị cũ sau x second

- Etag: là id duy nhất, client so sánh 2 Etag và sẽ download lại data nếu 2 eTag khác nhau
- LastModified:
