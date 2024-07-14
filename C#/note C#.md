# **note thập cẩm**

- phương thức Main luôn cần static, vì nó cần được gọi đầu tiên mà k phải tạo ra 1 instance
- cách tạo instance: instance = new className()

- ASP.NET dùng DI để quản lí vòng đời của các đối tượng
- DI sẽ tự tạo ra các đối tượng mà ta đã đăng kí

# câu hỏi lặt vặt

- NuGet là gì ?
  <!-- là trình quản lí package dành cho nền tảng .NET -->

- 2 cách thêm package
  <!-- chạy lệnh dotnet add package... hoặc tự thêm vào .csproj -->
  <!-- dotnet add package [Name] -->

- liên hệ giữa NuGet và file .csproj
  <!-- sau khi cài đặt gói x, thì x sẽ có trong file .csproj
  <ItemGroup>
    <PackageReference Include="x" Version="13.0.1" />
  </ItemGroup> -->

- bản chất, class là gì ?
<!-- là tập hợp các hàm -->

- chức năng của services.AddControllers() ?
<!-- đăng kí các dịch vụ cần thiết để làm việc với MVC Controller -->

- ASP.NET Core là gì ?

- chức năng của DI ?
<!-- liên kết controller -->

- làm sao để dùng service trong controller ?
<!-- đăng kí trong DI
structure trong controller dùng dc các service đã đăng kí trong DI -->

- Cách ASP.NET tự động liên kết
  <!-- http request đến
  -> Middleware Pipeline: dẫn request đi qua các middleware đã cấu hình trong Startup
  -> Routing Middleware: ánh xạ request đến endpoint tương ứng
  -> Endpoint Middleware: gọi method tương ứng trong controller
  -> Controller Activation: tạo instance của controller (bằng cách gọi contructor, và thêm các serice tương ứng) -->

- Container DI là gì ?

- DI (Dependency Injection) là gì ?
<!-- - là 1 design pattern,
- dùng để đạt IoC giữa class và dependence ?? -->

- compile time và runtime ?

- sự khác biệt giữa class và interface ?

- persistence class là gì ?

# OOP (Object-Oriented Programming)

- là mô hình lập trình

- là việc mô hình hóa 1 hệ thống thành 1 loạt các object,
- mỗi object đại diện 1 khía cạnh của hệ thống
- mỗi object gồm các hàm và data
- mỗi object đều có public interface (để tương tác với code ngoài) và internal interface (nội bộ)

- khi ta mô hình hóa 1 vấn đề theo hướng đối tượng, là ta tạo ra các định nghĩa trừu tượng đại diện cho các đối tượng ta muốn có trong hệ thống.

- class là 1 type, nó không có "sự sống"
- instance mới là thực thể thật sự

- hàm constructor dùng để tạo ra instance
- constructor có cùng tên với class

- constructor nhận vào các tham số, các tham số này tạo ra sự khác biệt giữa các instance

- ta có thể tạo ra class bằng việc extend từ class khác, để kế thừa các thuộc tính/phương thức của parent
- khi 1 object được tạo ra, nó thừa hưởng toàn bộ thuộc tính, phương thức của class đó

# SOLID

- mục đích của SOLID ?
<!-- - viết code dễ đọc, dễ test -->

- The *S*ingle Responsibility Principle
<!-- mỗi class chỉ nên làm "1 việc", 1 nhiệm vụ
mỗi class chỉ nên có 1 lí do để sửa lại class
(tức chỉ nên phụ thuộc vào duy nhất 1 thứ, và nếu phải sửa lại class thì chỉ có 1 lí do)
  -->
  <!-- ví dụ: 
  public class UserService {
    public void CreateUser(string name, string email) {
        // Code để tạo người dùng mới
    }

    public void UpdateUser(int id, string name, string email) {
        // Code để cập nhật thông tin người dùng
    }

    public User GetUser(int id) {
        // Code để lấy thông tin người dùng theo ID
    }

    public void DeleteUser(int id) {
        // Code để xóa người dùng theo ID
    }
} -->

- *O*pen-Close Principle ???
<!-- Class nên có khả năng: thêm feature mà k ảnh hưởng đến code cũ, và Close -->

- 
- The Dependency Inversion Principle (DIP)

# flow gán biến đơn giản
<!-- 
public class Invoice {  

	private Book book; // 1.KHAI BÁO BIẾN book
	

	public Invoice(Book book, int quantity, double discountRate, double taxRate) {
		this.book = book; // 2.TRUYỀN VALUE VÀO + GÁN CHO BIẾN BOOK
	}

}
 -->
# <!-- ^ 1 chương trình đơn giản nhất gồm những file nào ? -->

- Program.cs
  <!-- chứa hàm Main, chứa logic -->

- Startup.cs
  <!-- chứa class Startup: có các phương thức để cấu hình các dịch vụ, middleware, pipeline xử lí yêu cầu -->

- .csproj
<!-- chứa thông tin cần thiết để xây dựng dự án, quyết định cách thức biên dịch, triển khai dự án

bao gồm:
thuộc tính
các nuget package
tài nguyên -->

# <!--* các dịch vụ cần thiết để làm việc với MVC Controller ? -->

Action Invoker:

  <!-- dùng để gọi các method trong controller -->

Model Binding::

  <!-- giúp ánh xạ dữ liệu từ http request vào tham số của controller
  bao gồm việc xử lý dữ liệu từ query string, form data, route data -->

Model Validation

  <!-- - Kiểm tra tính hợp lệ của dữ liệu   -->

- Action Filters:
  <!-- thay đổi cách xử lí request/response ?? -->

- Authorization Filters
<!-- kiểm tra quyền truy cập của user ?? -->

- Exception Filters
<!-- xử lí các ngoại lệ -->

- Result Filters
<!-- xử lí result trước khi gửi về client ? -->

- Routing
  <!-- phân tích http request và ánh xạ đến controller tương ứng -->

- Formatter
<!-- đọc và ghi dữ liệu trong các định dạng khác nhau (XML, JSON,...) -->

- Dependency Injection (DI)
<!-- cho phép thêm các dịch vụ khác vào controller -->

- Controller Activator
<!-- tạo ra instance của controller khi có yêu cầu -->

- Controller Factory
<!-- chịu trách nhiệm tạo ra instance của controller -->

# <!--^ cú pháp: public IConfiguration Configuration { get; } -->

public IConfiguration Configuration { get; }

  <!-- modifier  type                  propertyName        {accessor của thuộc tính} -->

