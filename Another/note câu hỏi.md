- lí do không thể dùng useMemo thay thế cho memo ??

- khi UI đang được render, và state tiếp tục update thì sao ???
  <!-- update state khi rendering chỉ được phép trong chính component của nó, và pattern này hầu như không được dùng -->
  <!-- https://react.dev/reference/react/useState#setstate-caveats -->

- state của parent truyền vào child, khi state change --> parent re-render --> child re-render 2 lần: 1 vì parent re-render , 1 vì props change ? có phải không?
<!-- Không, chỉ re-render 1 lần, (theo thực tiễn) -->

- useEffect là async func hay sync func ?
<!-- useEffect là hook, cho nên k có khái niệm async và sync ở đây -->

- dùng console để so sánh các object value giữa các lần re-render ??

- --save, --dev ý nghĩa ??
