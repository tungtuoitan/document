


# cách dùng modifier
cách dùng access modifier
public: dùng cho các controller method, này là bắt buộc, nếu k dùng thì ASP.NET Core framework k gọi chúng để xử lí request dc

private:
dùng cho những phương thức riêng tư, chỉ cho bà con sử dụng chúngvd: logger service, các biến chứa service bên ngoài
khi viết đè method, thì phải dùng lại access modifier

protected
khi ta muốn data x chỉ được dùng trong class cha và class con của nó, và k thể truy cập x trong các class khác
diff giữa protected và private:
private k thể truy cập từ con
protected có thể truy cập từ con

cách dùng modifier
static
dùng để chỉ định thành viên đó thuộc về class, chứ k thuộc về instance/object
dùng cho biến toàn cục, tức biến dùng chung (vd: count
dùng cho các hàm trong class gọi trực tiếp mà k cần tạo object (vd: hàm tiện ích utility...)
dùng với class để tạo class tĩnh (vd: class tiện ích...)
dùng với phương thức Main() 

readonly
dùng để chỉ định rằng sau khi được gán, thành viên này k thể thay đổi/ gán lại
(vd: dùng cho các biến chứa repository/filter service,... những biến này thường dùng private readonly

quy tắc
1 thành viên chỉ có thể có 1 access modifier
có những modifier k thể kết hợp với nhau vì mâu thuẫn về logic (vd: private public)
các kết hợp phổ biến (public static, private readonly, protected virtural
class có tối đa 2 modifier, còn field/method/property có thể có tối đa 3 modifier



#
Unit testing
testing framework phổ biến là MSTest
https://www.youtube.com/watch?v=WKZy9VX-kik
test được các hàm, và hoạt động của các api nữa
trong be, 1 service tương ứng với 1 project trong solution (nhưng k phải project nào cũng là service, vd repo project, model project...)

OOP
vanthiel.be dùng nguyên tắc OOP vì, be được chia thành từng cục: SampleRequestController, SampleRequestService, ...