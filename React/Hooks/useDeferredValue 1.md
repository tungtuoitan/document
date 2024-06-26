# useDefferredValue

- deferredValue = useDeferredValue(input)

## dùng để làm gì?

- tối ưu performance khi state bị update liên tục bằng cách chỉ update UI 1 lần duy nhất, thay vì update UI liên tục, fetch liên tục

## update UI 1 lần duy nhất bằng cách nào ?

- bằng cách thay đổi cách re-render của component khi input thay đổi

## cách re-render của component (có dùng useDeferredValue) khi input thay đổi

- khi input thay đổi:

- re-render1: re-render k update deferred input, dẫn đến không update UI
- re-render2: re-render có update deferred input, nhưng có thể bị hủy ngang và bị đè lên
  (khi chuỗi update input kết thúc, re-render2 cuối cùng sẽ hoàn thành và UI được update)

## lưu ý khi dùng:

- Khi dùng với Transition thì useDeferredValue sẽ luôn trả về new value và k tạo ra background re-render......
- useDeferredValue chỉ "trì hoãn" update UI chứ không "trì hoãn" request
- nếu input là object được tạo mới trong rendering thì sẽ tạo ra re-render không cần thiết
- khi dùng với Suspense thì React vẫn show UI của input cũ trong khi đang "typing" chứ k show fallback
- re-render2 xảy ra ngay sau re-render1, và không có delay
- re-render2 xảy ra bên ngoài re-render1 (re-render chính), nên không bao giờ làm "treo" UI, nên còn được gọi là "background re-render"
- trong re-render2, Effect chỉ chạy sau khi UI đã được update

## các kịch bản phổ biến

- show UI cũ khi đang load UI mới
- cho user biết rằng app đang LOADING data mới
- Trì hoãn UI "nặng" để ưu tiên UI "nhẹ"

