# useState

const [state, setState] = useState(param)

# chức năng

- thêm 1 state

# name convention

- [something, setSomething] = useState

# lưu ý khi dùng:

- setState chỉ update state cho next render, nên sau dòng code update, state vẫn mang old value
- nếu new state giống old state (React so sánh bằng Object.is()) thì component và child sẽ không được render. Mặc dù trong 1 số trường hợp comoponent sẽ được render nhưng child thì không

- event handler run --> queue run để update state --> re-render
- khi dùng 3 setState(count +1), thì vẫn chỉ tương đương 1 setState(count +1) vì việc việc update state không diễn ra ngay lập tức mà diễn ra sau cùng
- cách thức react update state
<!-- https://react.dev/learn/queueing-a-series-of-state-updates#updating-the-same-state-multiple-times-before-the-next-render
https://react.dev/learn/queueing-a-series-of-state-updates#what-happens-if-you-update-state-after-replacing-it
https://react.dev/learn/queueing-a-series-of-state-updates#what-happens-if-you-replace-state-after-updating-it -->

## khi param là function

- param khi là function thì nó nên:
- nên pure
- không có tham số
- React sẽ gọi function đó khi khởi tạo component và lưu return value của nó làm initial state
- trong mỗi lần render, giá trị của state luôn fixed cứng
<!-- https://react.dev/learn/state-as-a-snapshot#rendering-takes-a-snapshot-in-time -->

# batching

- là hành vi react luôn đợi cho tất cả code của event handler thực thi hết rồi mới bắt đầu update state.

* điều này giúp ta update nhiều state, trong nhiều component mà không trigger quá nhiều re-render.
* điều này cũng có nghĩa là UI sẽ không được update cho đến khi tất cả code của event.handler chạy xong.

-React không gom nhóm nhiều event lại thành 1 (vd như chuỗi click), mỗi click là độc lập

# trong Strict Mode

- React sẽ gọi hàm Param 2 lần, (chỉ để check xem hàm có purity không)
- việc gọi 2 lần k ảnh hưởng gì cả

# setState(param2)

## khi param2 là function

- param2 được gọi là updater function

- nó phải pure,
- nên có 1 tham số là state hiện tại
- trả về next state

# sự khác nhau giữa việc dùng primitive param và function param trong setState

<!-- https://react.dev/reference/react/useState#updating-state-based-on-the-previous-state -->
