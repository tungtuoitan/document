# mô tả

- .NET framework
- mỗi source gồm nhiều solution, tức nhiều project

- solution email service gồm các project:
  emailserviceAPI
  emailServiceConsole
  EmailServiceLibrary

# Package References

(dùng thư viện bên ngoài để thực hiện chức năng cụ thể)

<!-- <PackageReference Include="AutoMapper" Version="10.1.1" /> -->

- Serilog
<!-- dùng để ghi log -->

- Microsoft.Extensions.Hosting
<!-- dùng để chạy background service -->

- AutoMapper
<!-- chuyển đổi dữ liệu từ các đối tượng khác nhau -->

- Microsoft.Extensions.Hosting.WindowsServices
<!-- cho phép chạy .NET core như 1 dịch vụ window -->

- Internet MIME
<!-- dùng để thao tác với tin nhắn MIME -->

- MsgKit (Version 2.4.3)
<!-- tạo file msg/ mail cho outlook -->
- Nuget là trình quản lí package,

# file .csproj

- file này không hiển thị trong solution explorer
- nằm trong thư mục gốc của dự án
<!--
<Project Sdk="Microsoft.NET.Sdk.Worker">

  <PropertyGroup>
    <TargetFramework>net6.0</TargetFramework>
    <UserSecretsId>dotnet-ClaimEmailReaderService-30AD8A2E-A574-4440-884A-501D1CF254E9</UserSecretsId>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="AutoMapper" Version="10.1.1" />
   ...
    <PackageReference Include="Serilog.AspNetCore" Version="4.1.0" />
  </ItemGroup>

  <ItemGroup>
    <ProjectReference Include="..\ClaimRepository\ClaimRepository.csproj" />
   ...
    <ProjectReference Include="..\ERPServiceLibrary\ERPServiceLibrary.csproj" />
  </ItemGroup>
</Project> -->

<!-- là file cấu hình của dự án
tham chiếu tới các dự án khác trong cùng 1 solution -->

# **bên trong EmailServiceAPI**

## Connected Services

<!-- chứa các dịch vụ bên ngoài (vd API bên ngoài) mà ứng phụ thuộc vào -->

- tại sao không thể mở được file Micro identity platform ??

- Property
- chứa các file cấu hình cho dự án
<!-- vd: launchSettings.json để cấu hình cho việc khởi động dự án -->

- controller
<!-- là các class chịu trách nhiệm xử lí yêu cầu của user -->

- Helper
<!-- là các class hỗ trợ, giúp đỡ dùng trong toàn bộ dự án -->

<!--! - Program.cs -->

chứa Main(), là điểm khởi đầu cho dự án

- Startup.cs

<!-- chứa cấu hình Middleware và khi khởi động -->

- CreateHostBuilder
<!-- dùng để cấu hình -->

# **Program.cs**

Main() -- CreateHostBuilder

đăng kí dịch vụ
các dịch vụ: caching, session, management, service để quản lí email, claims, ....

- AddSession
<!-- quản lí session trong ứng dụng -->

- HttpContext
<!-- cho phép truy cập vào request/response hiện tại từ bất kì đâu trong ứng dụng -->

- EmailService
<!-- xử lí tất cả các hoạt động liên quan đến email -->

- Claim
<!-- quản lí claim (lưu trữ, xử lí, ) -->

- DI Container
<!-- giúp quản lí services  -->
là thành phần trung tâm của ASP.NET Core

# **Dòng chảy từ Endpoint**
- xây dựng và cấu hình Host
- nhận request -- middeware -- các Dependency đã đăng kí -- (có session và cache phục vụ) -- Routing(hướng request đến controller/action cụ thể) -- 


AuditProdOrder
QCProdSKUGrid