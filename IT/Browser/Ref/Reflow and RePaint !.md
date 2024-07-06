# source

<!-- https://dev.to/gopal1996/understanding-reflow-and-repaint-in-the-browser-1jbg

 -->

# Diễn biến khi user enter url cho đến khi browser hiển thị UI

- nhập URL
- fetch đến server và nhận về file HTML, CSS
- Browser parse HTML code thành Token dạng <TagName, Atrribute, AttributeValue>
- Token được convert thành Node và được gắn vào DOM
- CSSOM Tree sẽ được tạo ra từ file css

- Xây dựng RenderTree:
- bắt đầu từ root của DOM, tính toán visible element và style của chúng (RenderTree sẽ bỏ qua các element như: meta, script, link, display:none,...)

- áp dụng CSSOM lên DOM

* CSSOM là đại diện cho tất cả css rules áp dụng vào document

- Reflow: tính toán vị trí và kích thước của các Node
- Repaint: paint renderTree lên màn hình

# khi nào Repaint được kích hoạt?
- diễn ra khi có sự thay đổi ảnh hưởng đến visiblity của UI (vd: visiblity, bgColor, outline...) nhưng không làm thay đổi Layout ??

# Reflow
- là tính toán lại vị trí, kích thước của element trong document ()

# khi nào reflow được kích hoạt? 
- khi có sự thay đổi ảnh hưởng đến vị trí/ kích thước của element

# lưu ý:
- khi  1 element reflow, nó sẽ dẫn đến flow tất cả child và ancester element của nó
- reflow và repaint đều là các hoạt động expensive

# điều gì dẫn đến reflow và repaint

# cách giảm tối thiểu repaint và reflow

# dung chrome dev tool để xem chi tiết repaint và reflow đã diễn ra