# **Tổng quan**

- được xây dựng dựa trên nguyên tắc OOP
- kết hợp nhiều tính năng của các mô hình khác nhau, đặc biệt là mô hình functional programming
- hầu hết các thư viện và .NET runtime được viết bằng C#
- hưởng lợi từ tính năng quản lí bộ nhớ tự động của .NET runtime
- C# cũng dùng các runtime library do .NET DSK cung cấp
- thuộc gia đình ngôn ngữ C (C, C++, Javascript, Java)
- là ngôn ngữ có type mạnh mẽ
<!-- compiler hoặc editting tool sẽ thông báo khi type sai -->
- top-level statement
<!-- cho phép viết code không cần Program class và Main method
compiler sẽ chuyển top-level statement thành Program class -->

- 1 chương trình gồm 1 hoặc nhiều file
- mỗi file gồm 0, 1, hoặc nhiều namespace
- mỗi namespace gồm các type như: class, struct, interface, enumeration, delegate, hoặc các namespace khác

## **type system**

- thư viện .NET class định nghĩa các type số có sẵn và các type phức tạp cho nhiều loại cấu trúc khác nhau
- các thông tin được lưu trong 1 type có thể gồm:
<!-- - không gian lưu trữ mà biến của type yêu cầu
- max/min value
- member (event, field, method...)
- base type
- interface -->

- sau khi khai báo type, ta k thể khai báo lại type

### 2 loại type

- type dùng struct là value type
- type dùng class, record là reference type

- image:
<!-- https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/types/#the-common-type-system -->

### type system trong .NET

- có 2 đặc điểm quan trọng:
- hỗ trợ kế thừa
- mỗi type trong common system type là value type hoặc reference type

### built-in type

<!-- https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types -->

### custom type

- là dùng struct, class, interface, enum, and record để tự tạo ra type

- .NET lib chứa 1 bộ custom type
<!-- https://learn.microsoft.com/en-us/dotnet/standard/class-library-overview -->

##

- Fundamental data types
- Generic
- Language integrated query (LINQ)
<!-- dùng để query / thao tác với data -->

- Task based asynchronous programming model
<!-- cho phép viết code async giống như sync -->

- await foreach statement
- pattern matching

- C# DevKit
<!-- giúp hiểu code C# và debug -->

# **các member**

## namespace

- namespace k thể chứa hàm, biến, mà chỉ chứa class à ?

## class

- dùng làm khung để tạo ra object,
<!-- object được tạo ra gọi là instance của class -->

- cách tạo class
<!-- dùng từ khóa new để gọi constructor
 Person person = new Person(); -->

- Định nghĩa class
  <!-- class là "type" của 1 object value cụ thể -->

  <!-- ví dụ:
  class Person
  {
      public string Name { get; set; }
      public int Age { get; set; }
  }
  int a = "xyz"
  Person person = new Person();

  Trong này:
  string là data type của    value "xyz"                             và biến a
  Person là data type của    value object(instance vừa được tạo)     và biến person
  -->

- vì sao phải khai báo biến chứa instance với className?
<!-- vì ta phải chỉ định kiểu dữ liệu của biến đó, vì trong C#, khi khai báo ta luôn phải khai báo type
vd:
int a = 3;
Person b = new Person();
ở đây int và Person đều là type
-->

## interface

## struct

# **data type**

## string

- verbaltrim string (chuỗi nguyên thủy)
  <!-- @"xxxx"
  trong verbaltrim string, ta thoải mái dùng các kí tự đặc biệt như ", /, @.... -->

- đánh dấu escape char
<!-- tương tự trong js -->

- chèn biến vào string bằng $ (string interpolation)
<!--
string message = $"My name is {name} and I'm {age} years old."; -->

- string formatting
  <!-- Console.WriteLine("my name is: {0}", name);
  Console.WriteLine("my age is: {0}", age); -->

- string concatenate
<!-- dùng + để nối 2 chuỗi
dùng string.Concate() để nối nhiều chuỗi -->

- ta không thể chuyển string kí tự thành number, mà chỉ có thể chuyển string dạng number thành number
<!-- sẽ gây ra lỗi -->

## khai báo

- khai báo với var
  <!-- c# sẽ tự động suy luận type của biến từ value được gán -->
  <!-- chỉ nên dùng var khi kiểu dữ liệu của biến đã RẤT RÕ RÀNG
  nếu không thì nên dùng các kiểu khai báo cụ thể, để code trở nên dễ đọc -->

- const
  <!-- dùng để khai báo hằng số
  const int a = 1;
  biến chỉ được dùng trong class/func chứa nó -->
  <!-- tình biên dịch tối ưu hóa bằng cách thay thế tất cả tham chiếu đến hằng số bằng giá trị trực tiếp của hàm số trong quá trình biên dịch
  nghĩa là const a = 20; Console.write(a);
  sẽ được chuyển thành:
  Console.write(20);
   -->

const int vat = 20;
int banlance = 1000;
Console.WriteLine(banlance \* (vat/100D));
trong ví dụ này ta phải dùng D để vat/100D là double (kq của thương là số thập phân), vì nếu không thì kết quả vat/100 sẽ là int (vì int/int) thì kq của thương sẽ là 0
và khi

## array

- log array ra thì chỉ nhận được type của array

- so sánh == sẽ so sánh tham chiếu của 2 đối tượng

## function

### cú pháp

[modifiers] return_type function_name([parameters])
{
// Mã thực thi của hàm
}

- return_type:
<!-- là type của return value
khi k trả về thì dùng void -->

# **modifiers**

## access modifiers

- gồm
<!-- public, private, protected, internal, protected internal -->

- chức năng:
  <!-- dùng để xác định phạm vi mà class/hàm/biến sẽ được sử dụng
  tức hàm, biến này sẽ chỉ được sử dụng trong assembly này, hay cả các assembly khác -->

- public
<!-- code của              mọi _assembly                                đều truy cập được type/member này -->

- private
<!-- chỉ có code trong     cùng class/struct                            mới có thể truy cập được type/member này -->

- protected
<!-- chỉ có code trong     cùng class/devired class                     mới có thể truy cập được type/member này -->

- internal
<!-- chỉ có code trong     cùng Assembly                                mới có thể truy cập được type/member này -->

- protected internal
<!-- chỉ có code trong     cùng Assembly/devired class                  mới có thể truy cập được type/member này -->

- private protected
<!-- chỉ có code trong     cùng Assembly và cùng class/devired class    mới có thể truy cập được type/member này -->

- file
<!-- chỉ có code trong     cùng 1 file                                  mới có thể truy cập được type/member này -->

- kiến thức thể hiện dạng bảng:
  <!-- https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers#summary-table -->

## non-access modifiers

### static

- dùng để khai báo 1 thành viên thuộc class đó, chứ k thuộc 1 object cụ thể nào
  <!-- do đó, thành viên static chỉ có thể được truy cập trực tiếp thông qua tên class -->

- trong C#, việc dùng static member trong non-static class phổ biến hơn là dùng static class
<!-- vì sao, best practice à ? -->

- 2 trường hợp phổ biến của static field trong non-static class là:
  đếm số instance được tạo ra và lưu trữ data được share giữa các instance

- các static member có thể overload ??, chứ k thể overide
<!-- vì chỉ có 1 phiên bản static member duy nhất -->

#### static member

- thành viên static luôn luôn phải được truy cập thông qua className, chứ k phải instance
  <!-- tức là khi khai báo static x, thì muốn dùng x ta phải gọi class.x -->

- chỉ có duy nhất 1 phiên bản static member được tạo ra, dù có bao nhiêu instance đi chăng nữa
<!-- vì static  member chỉ thuộc về class -->

#### static class

- chức năng:
<!-- dùng để chứa các phương thức, và các phương thức này chỉ dùng param chứ k dùng thành viên internal -->

- đặc điểm:
<!-- - chỉ có thể chứa thành viên static
- không thể tạo instance
- không thể chứa instance constructor
- bị sealed (tức k thể kế thừa) -->

- lợi ích:
  báo lỗi khi dev vô tình thêm thành viên vào class

### public

- dùng khi muốn sử dụng hàm/biến trong class khác

# **Note**

- vì sao trong C# luôn phải khai báo type ?

- không được định nghĩa phương thức trong 1 phương thức
- khi nhấn F5, chuyện gì xảy ra ?
<!-- C# sẽ tìm đến hàm Main trong class Program để chạy, đây là mặc định -->

- có tạo được class trong class không ?
- class rốt cuộc là gì?
- type của class là reference type ??

- tạo non-static class chỉ tạo duy nhất 1 instance:
<!-- https://learn.microsoft.com/en-us/previous-versions/msp-n-p/ff650316(v=pandp.10) -->

## workload

- là các tính năng nâng cao trong visual studio

## assembly

- là bộ sưu tập các type và resource được xây dựng để làm việc cùng nhau, để tạo nên 1 đơn vị chức năng

## .NET DSK

## ASP.NET Core web libraries

## .NET MAUI UI library

## console

### console.writeline()

- dùng để in ra giá trị
- Console.write()
<!-- Console.WriteLine("${0}, ${1}",number, name); -->

### console.readline()

- dùng để nhận vào giá trị user điền vào

## compiler ??

## thập cẩm

- console app
<!-- là app có command line -->

- .NET
<!-- - có 2 nghĩa:
framework .NET
develope flatform -->

- framework .NET
<!-- dùng để phát triển các ứng dụng chạy trên nền tảng window
phát triển ứng dụng web, dùng ASP.NET
phát triển ứng dụng di động, dùng Xamarin
-->

- namespace > class > static void

- int age = 23;
<!-- trong này,
int là integer (kiểu số nguyên)
int age: là declare
= 23: initialze -->

- int và long
<!-- - int32 và int64
int là kiểu int32 (32bit)
có range từ -2tr >> 2tr
- long:
  là int64, tức 64 bit
  có range lớn hơn, từ -9 tỉ >> 9 tỉ -->

- long number = 999999L;
<!-- mặc định trong C#, 1 int là kiểu mặc định nếu k được chỉ định type
thêm L vào để khai báo number là kiểu long,  -->

- tại sao cần khai báo kiểu long?
<!-- khi khai báo long thì number mới có thể thay đổi vượt ra khỏi value 2tr -->

- cw + Tab
<!-- shortcut của console.writeLine() -->

- double type vs float
  <!-- double:
  là kiểu double-precision floating point number
  có độ chính xác cao hơn, nhưng tốn không gian lưu trữ hơn
  chỉ dùng khi nào cần độ chính xác cao hơn
   -->
  <!-- float:
  là kiểu single-precision floating point number
  có độ chính xác thấp hơn, và tiết kiệm không gian lưu trữ

   -->

- decimal
<!-- có độ chính xác tuyệt đối
dùng trong tính toán tiền tệ, tài chính, khi không muốn sai số -->

- trong type, độ chính xác càng cao, thì càng tốn k gian lưu trữ

- int x; int y; int z; tương đương int x, y, z;

- đóng terminal là chương trình sẽ TẮT

- khi thay đổi value trong console.write() và hotload thì trong terminal k có thay đổi gì

- sự khác biệt giữa console.write() và console.writeline()
<!-- - write() sẽ viết tiếp trên 1 dòng
write sẽ xuống dòng và viết -->

- char và string
<!-- char dùng cho chuỗi 1 kí tự
string dùng cho chuỗi nhiều kí tự

char không được emty ('')
ngoặc kép "\_" dùng cho string
char dùng ngoặc đơn
-->

- bool
  boolean

- 3 cái này như nhau
<!-- age++
age = age + 1
age += 1 -->

- cộng 2 char
<!-- char ch = 'a'
ch += 'b'
trong ví dụ này, ch sẽ cho ra 1 kí tự ã, vì khi cộng 2 char,
nó sẽ cộng unicode của 2 char, sau đó quy đổi lại thành kí tự mới -->

- int i = 0;
Console.WriteLine(i++);
kết quả sẽ là 0
<!-- vì i sẽ được in ra trước, trước khi thực hiện phép cộng -->

- int a = 0001; tương đương với int a = 1
<!-- tức với number(int, double, float...) thì số 0 phía trước k có nghĩa gì -->

- tryParse
  dùng để kiểm tra việc chuyển đổi value type có thành công hay không, và chuyển đổi

# **.NET flatform**

## Class library
