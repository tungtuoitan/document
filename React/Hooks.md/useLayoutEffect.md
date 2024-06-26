# useLayoutEffect

- giống như useEffect, nhưng được kích hoạt trước khi browser re-paint

# chức năng

- dùng thay cho useEffect, khi ta muốn nó được kích hoạt trước khi browser paint, để user không thấy "tooltip moving"

# lưu ý khi dùng

- hãy dùng useEffect khi có thể, vì useLayoutEffect có thể dẫn đến performance problem

# layout measurement

# block browser re-paint

# useLayoutEffect làm block browser repaint, nhưng vì sao lại block?

- vì useLayoutEffect được kich hoạt trước khi browser repaint ??

# tại sao việc block browser repaint lại gây ra performance problem ?

- vì khi bị block, nghĩa là UI sẽ bị "lag", dẫn đến trải nghiệm k tốt

# Các kịch bản phổ biến

- thực hiện layout mesurement trước khi browser repaint

# lí do useLayoutEffect tồn tại

- hầu hết component không cần biết position và size của chúng để có thể render
- browser sẽ tính toán position và size của chúng để repaint

- nhưng có những trường hợp ta CẦN PHẢI BIẾT position và size của chúng: (ví dụ nếu width của nó < 100px thì sẽ nằm kế, còn nếu lớn hơn space thì phải xuống hàng)
- và những trường hợp này xả ra như sau:
- render tooltip ở bất cứ đâu (render sai vị trí cũng dc)
- đo kích thước để xác định vị trí của nó
- re-render nó ở vị trí chính xác

- quá trình này cần phải được xảy ra trước khi browser repaint, vì ta không muốn user thấy tooltip chuyển động
- do đó ta phải dùng useLayoutEffect trong trường hợp này

# Troubleshooting
<!-- https://react.dev/reference/react/useLayoutEffect#im-getting-an-error-uselayouteffect-does-nothing-on-the-server -->