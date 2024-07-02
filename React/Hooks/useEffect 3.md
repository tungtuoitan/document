# useEffect

useEffect(setup, dependencyArr)

# hoạt động của useEffect

- khi component được thêm vào DOM , hàm setup sẽ được thực thi:
- sau khi re-render, nếu dependency thay đổi thì:

* 1. thực thi clean up function với value cũ,
* 2. thực thi setup function với value mới (hầu hết là sau khi browser paint)

- sau khi component được move khỏi DOM thì clean up function được thực thi

## hoạt động của useEffect trong Strict Mode

- mỗi lần phải run, thì setup run --> clear func run --> setup run
- 2 hàm đầu tiên chạy là để test ....

## dependency array

- phải chứa tất cả các [reactive value] có trong setup function,
- react sẽ so sánh các dependency với các giá trị trước đó bằng Object.is()
- khi không cung cấp dependency array, setup sẽ chạy lại sau mỗi lần render
- khi dependency array [] rỗng, hàm setup chỉ chạy đúng 1 lần

# chức năng

- cho phép thực hiện side effect trong component mà vẫn giữ cho component pure

# thời điểm thực thi hàm setup

> > Triggering

- update state/props...
- tạo ra queue render

> > Rendering

- chạy component function để tạo JSX (đây là hoạt động đệ quy)
- so sánh với preJSX để tìm ra những chi tiết cần update

> > Committing (tức React commit change to DOM)

(là giai đoạn áp dụng những chi tiết cần thay đổi vào DOM)

- update DOM

_RUN setup in useEffect synchronously khi việc show lastest UI là quan trọng (hiếm khi xảy ra)_

> > paint screen (tức browser rendering)

**RUN setup in useEffect asynchronously (most of the time)**

# ví dụ các hoạt động side effect

- tạo kết nối đến server
- control non-React component
- fetch API
- tương tác với browser API
- thao tác DOM 1 cách thủ công

# clean up function

dùng để thực hiện các hoạt động "dọn dẹp" như:

- dừng timer đang chạy
- đóng kết nối đến server
- giải phóng tài nguyên
- hủy bỏ event listener khi component bị hủy
- xóa side effect

# lưu ý khi dùng

- khi hàm setup không chứa side effect thì không cần dùng useEffect

- ta không thể tùy ý chọn dependency, dependency được quyết định bởi code trong component
- để remove dependency, ta phải "chứng minh" cho linter thấy là: dependency đó không cần thiết
- khi linter báo lỗi chỗ dependency[], tức nó có thể gây ra bug, và dùng "// eslint-ignore-next-line react-hooks/exhaustive-deps" không có ích gì cả

- chưa hiểu:
  <!-- "When Strict Mode is on, React will run one extra development-only setup+cleanup cycle before the first real setup. This is a stress-test that ensures that your cleanup logic “mirrors” your setup logic and that it stops or undoes whatever the setup is doing. If this causes a problem, implement the cleanup function. -->
  <!-- https://react.dev/learn/synchronizing-with-effects#how-to-handle-the-effect-firing-twice-in-development -->

- khi dependency là các function/object được định nghĩa trong component, nó có thể dẫn đến re-render không cần thiết. để giải quyết điều này, ta cần tìm cách move các function/object đó ra, có thể bằng cách di dời <update-state logic> và <non-reactive logic> ra khỏi hàm setup

- Khi Effect có thao tác với UI, và nếu UI đó có lg hay gì thì dùng useLayoutEffect để thay cho useEffect.

- trong trường hợp Effect chạy trước khi painting, và ta muốn Effect chạy sau, thì ta có thể dùng setTimeout
<!-- (https://github.com/reactwg/react-18/discussions/128) -->

- "chưa hiểu":
  <!-- Even if your Effect was caused by an interaction (like a click), React may allow the browser to repaint the screen before processing the state updates inside your Effect. Usually, this works as expected. However, if you must block the browser from repainting the screen, you need to replace useEffect with useLayoutEffect. -->
  <!-- https://react.dev/reference/react/useEffect#usage -->

- Effect chỉ chạy ở client

- [cố gắng viết Effect thành 1 process độc lập và riêng tư]
<!-- https://react.dev/learn/lifecycle-of-reactive-effects#each-effect-represents-a-separate-synchronization-process -->

- [luôn focus vào setup/cleanup cycle đơn lẻ và không nhìn theo view của Effect]
<!-- https://react.dev/learn/lifecycle-of-reactive-effects#thinking-from-the-effects-perspective -->

# Các kịch bản phổ biến:

- Connect đến server
- wrapping Effect in custom Hook

* custom Hook:
    <!-- function useChatRoom({ serverUrl, roomId }) {
    useEffect(() => {
        const options = {
        serverUrl: serverUrl,
        roomId: roomId
        };
        const connection = createConnection(options);
        connection.connect();
        return () => connection.disconnect();
    }, [roomId, serverUrl]);
    } -->
* sử dụng custom Hook:
  <!-- function ChatRoom({ roomId }) {
    const [serverUrl, setServerUrl] = useState('https://localhost:1234');

    useChatRoom({
      roomId: roomId,
      serverUrl: serverUrl
    });
    // ... -->

- update state bằng setInterval
<!-- ví dụ: https://react.dev/reference/react/useEffect#updating-state-based-on-previous-state-from-an-effect -->

- loại bỏ object/function trong dependency để tránh re-run nhiều lần

- Reading the latest props and state from an Effect (đang phát triển)
<!-- https://react.dev/reference/react/useEffect#reading-the-latest-props-and-state-from-an-effect -->

- Control a non-React widget
<!-- https://react.dev/reference/react/useEffect#controlling-a-non-react-widget -->

- ta cần hiển thị content ở client khác với ở server khi dùng SSR (trường hợp hiếm)
<!-- react.dev/reference/react/useEffect#displaying-different-content-on-the-server-and-the-client -->

## Troubleshooting

- Effect chạy 2 lần khi component mount (là do Strict mode)

- Effect run sau mỗi re-render (do chưa thêm dependency [], hoặc dependency thay đổi mỗi lần re-render)

- Effect chạy hoài không dừng (do Effect đã update someState, và someState làm thay đổi dependency)
<!-- https://react.dev/reference/react/useEffect#reading-the-latest-props-and-state-from-an-effect -->

- hàm clean up run mặc dù component không unmount
<!-- https://react.dev/reference/react/useEffect#my-cleanup-logic-runs-even-though-my-component-didnt-unmount -->

- UI bị nhấp nháy trước khi Effect run
<!-- https://react.dev/reference/react/useEffect#my-cleanup-logic-runs-even-though-my-component-didnt-unmount -->

## fetch data

# Another

## tại sao dependency lại cần chứa tất cả reactive value trong setup function?

- dependency nên chứa tất cả biến liên quan có trong side effect, để đảm bảo khi các biến thay đổi thì side effect được thực hiện lại để kq up-to-date
