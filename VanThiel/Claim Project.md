# **Plan**

## các việc cần làm

<!-- - _source code: slideFilter_ -->
<!-- - _source code: flow code_ -->
<!-- - token cơ bản -->
<!-- - source code: token -->

- học sourcetree cơ bản
- source code: screen QC APP
- source code: common component
- source code: all FE technology
- tối về nhờ Renel thêm IP của nhà mình vào,
- liệt kê lại tất cả thủ tục khi đi làm , từ khi nhận task cho đến update status

### học dần dần

- học tool (itsm)
- ứng xử
<!-- trò chuyện buổi trưa, chat nhóm, chat với sếp, nc với team bên ngoài -->
- cấu trúc nhân sự của công ty
- đọc source code
<!-- tìm hiểu screen SKU -->
- setup autoHotKey

# cấu trúc file

- dataLoader:
<!-- chứa các hàm load data -->

- targetPrice:
  <!-- chứa các hàm callback xử lí sau dataLoader -->
  <!-- các hàm này chứa window.fetch -->

- utilities.js
<!-- chứa các hàm hỗ trợ -->

## costingSupplier

# **Flow của TargetPrice**

- load data bằng api

## chức năng

- xem sản phẩm
- toggle priceFilter popup

- loadProductMasterDropdown >>
  là load tất cả "dạng data" liên quan đến product như: status, launch session ??,

# **token**

- là string đại diện cho quyền truy cập, quyền xác thực
- dùng để xác minh danh tính user/client

- access token:
- là token được cấp cho user sau khi xác thực thành công
- thường được đính kèm trong header Authorization

- refresh token:
- được cấp kèm theo access token
- được dùng để refresh khi access token hết hạn

- hoạt động
- user đăng nhập, gửi account đến server
- server xem xét account được gửi đến và tạo ra access token + refresh token
- user fetch các API bảo mật thì đính kèm access token, thì mới thành công

- khi access token, user gửi refresh token đến server, server sẽ cấp access token mới cho user

- token luôn gắn liền với 1 account cụ thể
- mỗi token có 1 phạm vi quyền hạn cụ thể

- access token có thời gian sống vài giờ - vài ngày
- refresh token có thời gian sống vài ngày - vài tuần, tùy theo cấu hình

## các thư viện liên quan

- (MSAL)
- @azure/msal-react
<!-- cho phép React xác thực user bằng Azure id, microsoft acc -->
- @azure/msal-browser

- @microsoft/signalr
- @wojtekmaj/react-hooks
- dexie-react-hooks

## khái niệm

- Azure ID
  <!-- là nhà cung cấp xác thực -->
  <!--
  nhà cung cấp xác thực là: server lưu trữ thông tin user,
  client sẽ fetch đến authentication server và
  authentication server sẽ trả về token
  -->

- Web storage
<!-- gồm 2 loại: local storage và session storage -->

## các hoạt động xác thực trong Claims

- const { instance, accounts } = useMsal();
- instance
<!-- là đối tượng MSAL, tức thư viện -->
- accounts
<!-- chứa thông tin về accounts đang đăng nhập hiện tại, hoặc đã đăng nhập -->

- instance.loginRedirect()
<!-- chuyển hướng dến trang đăng nhập của Microsoft -->

- user nhập account và click login >> gửi request
- authentication server xác thực và gửi về token + refresh token

- instance.acquireTokenSilent()
  <!-- lấy token 1 cách "lặng lẽ"
  nếu trong cache còn token, và token này chưa hết hạn thì nó sẽ lấy,
  nếu k có token, hoặc hết hạn thì sẽ dùng refresh token để làm mới, nếu refresh token còn hiệu lực,
  nếu k có cả 2 token, hoặc cả 2 hết hạn thì sẽ throw error  -->

## diễn biến khi vào webpage /targetPrices

- useMsal()
-

- instance.acquireTokenSilent()
  <!-- lấy new token và email (bằng cách gửi đi refresh token)
   1 cách "im lặng" khi đã có 1 phiên đăng nhập trước đó-->

  truyền vào account của user

- isAuthorized()
<!-- check xem user đã được xác thực hay chưa

bằng cách gửi email+token đến server ,
nếu chưa thì cút,
nếu có thì lưu lại userData -->

## diễn biến TargetPriceForm

- loadProductMaster

## <!-- tại TopNavigation, trong useEffect(), ngay khi vào web -->

- getUserAccess
<!-- fetch đến server để lấy ... -->

- getUserAccessData()
<!-- lưu userData vào Auth Store, bằng setAuth() -->

## quy trình login của toidicodedao

- lấy id + secret ??
<!-- bằng cách tạo app, và đăng kí với microsoft -->

- dẫn user đến auth.google/id=xxx

- lấy token
<!-- - gọi api đến microsoft server, gửi đi: code + secret + url, và microsoft server sẽ cho ta token  -->

# **another**

## mục đích của các funciton

- getCurrentComponentLinks()
<!-- update url trên header

-->

- navigationStore
<!-- update url trên header -->

## câu hỏi

- header được quyết định bởi ai ??
- flow của token ??
- token này có thời gian sống bao lâu ?
- tại sao lại k lưu token trong trình duyệt, mà phải dùng aquireTokenSilent()
- mình không dùng eslint, format tool phải không ?
- dùng jwt.com để đọc thông tin từ token

## flow chính

TopNavigation2

<!-- TopNavigation -->

- navigation:
<!-- - SideNavigation2 -->

- TargetPricesContainerLazy
- TargetPricesContainer
- TargetPriceToolbar
