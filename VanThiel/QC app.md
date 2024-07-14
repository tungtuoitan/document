# **Plan**

## các việc cần làm

- học sourcetree cơ bản

### học dần dần

- setup autoHotKey

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

# **AAD / Azure Active Directory / Azure AD**

- là đơn vị quản lí user, quyền hạn user và xác thực user
- là xương sống của Microsoft Office 365

## chức năng

- quản lí user và quyền hạn user
- xác thực user

## cách dùng AAD trong 1 dự án

- tạo Azure AD tenant ở portal.azure.com
<!-- cái này đại diện cho tổ chức của mình, và ta sẽ quản lí user thông qua tenant -->

- tạo id cho app trong AZure AD tennant

- cấu hình xác thực và truy cập
  <!-- tức là chọn kiểu xác thực (vd: đăng nhập thông qua Azure AD, OpenID Connect hoặc OAuth)
  và xác định quyền truy cập cho từng loại user
  -->

- Tích hợp Azure AD vào app
  <!-- - tức ta sẽ dùng Azure AD thông qua thư viện MSAL -->
  <!-- cụ thể, ta sẽ login/logout/xác thực thông qua các hàm mà MSAL cung cấp -->

## hoạt động của AAD server

- khi user đăng nhập vào web, sẽ được chuyển hướng đến trang đăng nhập của AAD
- sau khi AAD xác thực xong, sẽ chuyển hướng về trang web cụ thể (được khai báo trong cấu hình)

- Admin vào Azure AD tennant để quản lí user và quyền hạn của user

## thành phần AAD trong code

- thư viện MSAL

* <MsalProvider> và PublicClientApplication
  <!-- cung cấp data xác thực và chức năng xác thực cho các component bên trong -->
  <!-- ví dụ:
  phương thức: login, logout, getToken?
  data xác thực: token, email user,... -->

- MS Graph API
<!-- cho phép ta tương tác với Azure Active Directory -->

- azure/msal-react
  <!-- * cung cấp:
  MsalProvider component để cung cấp context (data và phương thức) cho các component bên trong
  useIsAuthenticated: trả về boolean, cho biết là tình trạng xác thực/chưa xác thực,
  useMsal: để lấy data accounts, token... -->

# **Realtime**

- là update data mỗi khi thời gian thay đổi

## cách dùng SignalR để tạo realtime

- cài đặt SignalR ở BE
- xác định hub
- đăng kí và cấu hình SignalR
- dùng SignalR để gửi và nhận realtime

## Hub

- là 1 class ở backend, dùng để gửi và nhận tin nhắn realtime
<!-- https://stackoverflow.com/a/8929826 -->

## dùng signalR ở app

- HubConnection
  <!-- đại diện cho 1 kết nối đến hub -->
  <!-- cung cấp phương thức để gửi và nhận tin nhắn realtime -->

- HubConnectionBuilder
<!-- - tạo đối tượng HubConnection -->

- HubConnectionState
<!-- đại diện cho trạng thái kết nối -->

# **wojtekmaj/react-hooks**

- useResizeObserver()
<!-- dùng để theo dõi sự thay đổi kích thước của element trong DOM -->

# **Dexie / dexie-react-hook**

## tổng quan

- được thiết kế để làm việc với indexedDB API
- sử dụng Promise để thực hiện các hoạt động bdb
- dùng schema để định nghĩa cấu trúc dữ liệu
- hỗ trợ nhiều kiểu query (filter, sorting, pagination...)

## chức năng

- giúp thao tác với indexedDB API dễ dàng

# **IndexedDB API**

## tổng quan

- là 1 low-level API có sẵn trong trình duyệt
- có khả năng truy vấn, CRUD (ngay cả khi offline)
- data được lưu dưới dạng key-value
- là 1 phần của Web Storage API
- việc dùng indexedDB trực tiếp sẽ làm code phức tạp, do đó Dexie ra đời để viết mã đơn giản hơn
- là 1 js object db
<!-- tức nó là 1 đối tượng js ?? -->
- dùng để lưu trữ 1 lượng data lớn có cấu trúc ở client
- data được lưu trữ trong trình duyệt, tại vị trí:
<!-- C:\Users\<username>\AppData\Local\Google\Chrome\User Data\Default\IndexedDB -->

- ta có thể xem indexedDB trong chrome dev tool

- data trong indexedDB chỉ bị mất khi ta chủ động xóa nó, hoặc xóa dữ liệu trình duyệt,
<!-- khi đóng tab, mất mạng thì data vẫn còn nguyên -->

## chức năng

- cache data của server
- cho phép truy xuất data offline
- cho phép truy xuất data mạnh mẽ

# **another**


# **quy trình làm việc**

## nhận task

- tìm hiểu requirment
- update status: in progress
- update task type: deployment

## coding

## self-test

## push lên master-dev

- pull tất cả các nhánh

- tạo nhánh mới
  <!-- đặt tên theo cú pháp LT-QC-master-dev-01-09-00-700
  coding... -->

- đẩy code mới lên remote/master-x-dev bằng cherrypick

- đẩy code mới lên remote/master-dev bằng cách merge từ master-x-dev (hay remote/master-x-dev)

## đẩy lên dev-portal

## test trên dev-portal

## update status

- nhớ chèn hình ảnh, có red rectangle
- khi test xong thì task type chọn NONE

# **task700**

- page1.
<!-- QCProdOrderGrid -->

- page 2
<!-- QCProdOrderGridHelper -->

- page 3
<!-- AuditSKUInfo (tương ứng với 1 item) -->

- 4: hàm mở ra window
<!-- SKUWindowEvents -->

- component chứa header
<!-- SKUContainer -->

triggerSKUWindow

- hàm toggle
<!-- onClickSKUInfo -->

- biến toggle window:
<!-- openSKUs trong SKUContainerHelper -->

##

- tại sao khi triggerSKUWindow() thì window mở 1 cái mới ?
- window được dùng ở rất nhiều nơi

<!--
MainBody
 >> MainProductMasterWindows//useSKUDialogHelper >>>>>> PLMProductMasterWindows >> PLMProductMasterWindow >> SKUContainer >>
ToolbarMenu
 -->

khi click:::
adjustWindowPropsAndZIndex

> > openSKUDetail

> > setSKUDetails
> > setOpenSkuWindow
> > openSkuWindow >> opened={openSkuWindow}

- setSKUDetails

(tất cả nằm trong SKUDetailStore)

<!-- trong PLMProductMasterWindows, array SKUDetail sẽ render ra 1 loạt các window -->


# **QC APP**

- dùng để ghi chú lại việc kiểm tra sp

- Tester sẽ kiểm theo từng Batch, mỗi Batch gồm nhiều sp
  mỗi Batch tương ứng 1 Report

##

- SEARCH -- order -- sp
<!-- search chứa các Order, gồm nhiều sp, từ sp ta có thể thấy được Report -->
- AUDIT -- QC report -- sp
  <!-- audit chứa các report chưa test -->
  <!-- tester sẽ kiểm tra và update report tại đây -->
- REPORTS -- report (tương ứng 1 QC report)
  <!-- Report chứa các report đã test -->
  <!-- tại đây, ta có thể tải report, cho report về pending lại, để test lại -->

- ta chỉ có thể xóa report chưa test và report đang pending (chuẩn bị test), còn report đã test thì không thể xóa ??
<!-- - mình chỉ quan tâm đến status của 2 list: audit Report và tested Report -->

## ghi nhận thực tế khi check app

- khi xóa Pending thì list k refresh, số lượng Pending cũng không,

## Phân nhỏ Task

- khi xóa ở SEARCH
  thì Audit hặc Report update, và Order sẽ update, số lượng Audit phải update
<!-- CHƯA OK -->

<!-- - khi tạo report ở SEARCH 
thì Order update, và Audit update
     DONE   -->

<!-- - khi xóa ở AUDIT thì 
  Audit list sẽ update -->
<!-- DONE -->

<!-- - khi xóa ở Report thì 
  Report sẽ update -->
<!-- DONE -->
