# useDefferredValue

## lí thuyết

- deferredValue = useDeferredValue(input)
- deferredValue là 1 "phiên bản trì hoãn" của input

## dùng để làm gì?

- "trì hoãn" việc updating UI bằng cách thay đổi cách re-render của component khi input thay đổi
- tối ưu performance bằng cách chỉ update UI 1 lần duy nhất, thay vì update UI liên tục, fetch liên tục
  "trì hoãn": vẫn hiển thị UI cũ cho đến khi UI mới load xong

# cách re-render của component (có dùng useDeferredValue) khi input thay đổi

- re-render1: re-render mà k update deferred input, dẫn đến không update UI
- sau đó, "cố gắng" re-render với new value (tức là [lập lịch])
- "cố gắng": ngay sau khi kết thúc re-render1, background re-render bắt đầu ngay lập tức. Nếu lần re-render này hoàn tất thì UI được update, Nhưng nếu chưa hoàn tất và có background re-render mới thì background re-render hiện tại sẽ bị hủy và bị background re-render mới ghi đè lên.
  ("background re-render" sẽ render như thông thường NHƯNG có update deferred input)

## React xác định input có thay đổi hay không bằng cách nào ?

- React dùng Object.is (tức shallow comparision)

## syntax

<!-- https://react.dev/reference/react/useDeferredValue#parameters -->

## lưu ý khi dùng:

- Khi dùng với Transition thì useDeferredValue sẽ luôn trả về new value và k tạo ra background re-render
<!-- - [không hiểu đoạn này trong link: https://react.dev/reference/react/useDeferredValue#parameters??]
- The background re-render caused by useDeferredValue does not fire Effects until it’s committed to the screen. If the background re-render suspends, its Effects will run after the data loads and the UI updates.-->
- useDeferredValue chỉ "trì hoãn" update UI chứ không "trì hoãn" request
- value truyền vào useDeferredValue phải là primitive value, hoặc object, nhưng object phải không được thay đổi ở mỗi lần render (Vì nếu vậy thì sẽ tạo ra thêm 1 lần re-render không cần thiết)

- cụ thể: mỗi khi input thay đổi, React sẽ [lên lịch] để re-render (gọi là background re-render), và nếu đã có lịch update trước đó, thì nó sẽ hủy lịch trước đó và lên lịch lại từ đầu.

- useDefferedValue hoạt động tốt với Suspense, cụ thể: khi có update, user sẽ không thấy fallback, mà sẽ thấy UI của data cũ trong lúc chờ update data mới

- re-render với deferredValue xảy ra ngay sau khi kết thúc hoạt động re-render mặc định, và không có delay

## các kịch bản phổ biến

- show UI cũ khi đang load UI mới
<!-- https://react.dev/reference/react/useDeferredValue#showing-stale-content-while-fresh-content-is-loading -->

- cho user biết rằng app đang LOADING data mới
<!-- https://react.dev/reference/react/useDeferredValue#showing-stale-content-while-fresh-content-is-loading -->

- Trì hoãn việc re-render 1 phần UI "nặng",
(việc update UI "nhẹ" và update UI "nặng" diễn ra "cùng lúc", nên UI nhẹ sẽ bị lag, để giải quyết vấn đề này, ta dùng useDeferredValue() để cho phần re-render UI "nặng" thành background re-render, thì việc update UI "nặng" sẽ diễn ra sau cùng, tức ưu update UI "nhẹ" diễn ra trước --> hết lag)
<!-- https://react.dev/reference/react/useDeferredValue#deferring-re-rendering-for-a-part-of-the-ui -->

## trì hoãn 1 value khác với debounce và throttling thế nào?....

- debounce: chuỗi typing - chờ 1s (không có typing diễn ra trong 1s này) - update
- throttling:......
- defering tốt hơn trong việc tối ưu hóa rendering, vì nó tích hợp với React và thích ứng với user's device
- defering không có fixed delay
  (tương thích với user's device: tức khi device ngon thì defering giống như "không trì hoãn", còn device yếu thì defering sẽ có độ trì hoãn tương ứng)
- khi đang rendering 1 list dài, và user typing thêm, thì react sẽ hủy việc re-rendering đó và bắt đầu lại từ đầu. còn debounce và throttling thì không

## source

<!--  https://www.youtube.com/watch?v=yIpHTYo3PY0 -->
