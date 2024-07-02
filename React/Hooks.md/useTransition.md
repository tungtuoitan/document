# useTrasition

const [isPending, startTransition] = useTransition();

# chức năng

- cho phép ta update state mà không block UI

## block UI (v)

- làm đóng băng UI (tức bị lag)

# isPending

- là biến mang trạng thái của transition: "đang transitioning"/ "NO"

# startTransition()

- dùng để đánh dấu các update state bên trong là [Transition]

## transition / non-blocking transition

- là sự update state mà không block UI

## đặc điểm trasition

- không block UI (tức không cản trở sự update state/update UI khác)
- không hiển thị [indicator]

## đặc điểm của transition

- sự update state sẽ được [lên lịch] và đồng bộ ??
- việc update này là low priority, tức là các update khác chạy xong hết rồi thì isPending = true, và transition mới được thực hiện
- tức là khi

### loading indicator / chỉ báo tải

- là các animation thể hiện là data đang được load

## non-blocking transition

-

## tham số scope trong startTransition

- là 1 hàm chứa setState để update state
- React sẽ gọi scope ngay lập túc và đánh dấu sự update state
  React immediately calls scope with no parameters and marks all state updates "scheduled synchronously??" during the scope function call as Transitions.

- đánh dấu tất cả state trong startTransition là low-priority

# lưu ý khi dùng

- chỉ dùng khi code gặp vấn đề về performance, (vì khi dùng, thay vì render 1 lần, React sẽ render đến 2 lần)

# các kịch bản phổ biến

- đánh dấu state update là [non-blocking Transition]
- update state của parent bằng useTransition()
<!-- https://react.dev/reference/react/useTransition#updating-the-parent-component-in-a-transition -->
- hiển thị pending visual state trong quá trình transition
- ngăn ngừa các [loading indicator] không mong muốn
- dùng Transition với Suspense
<!-- https://react.dev/reference/react/Suspense#preventing-already-revealed-content-from-hiding -->

- build suspense-enabled router
  <!-- https://react.dev/reference/react/useTransition#building-a-suspense-enabled-router -->

- Hiển thị Error kèm theo error boundary
<!-- https://react.dev/reference/react/useTransition#displaying-an-error-to-users-with-error-boundary -->

# Troubleshooting

<!-- https://react.dev/reference/react/useTransition#troubleshooting -->
