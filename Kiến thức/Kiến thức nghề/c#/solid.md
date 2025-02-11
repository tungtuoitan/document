

# SOLID
link kiến thức: https://www.youtube.com/watch?v=kF7rQmSRlq0


single responsibility
  class đó nên có trách nhiệm giải quyết 1 cụm vấn đề duy nhất. có nghĩa là, tức 1 class chỉ nên gồm 1/nhiều hàm liên quan đến 1 cụm vấn đề đó
k có nghĩa là 1 class có 1 hàm, mà 1 class chứa nhiều hàm liên quan

Open /close
open: tức class có khả năng mở rộng (bằng cách kế thừa class) và k dc thay đổi code cũ (close)

Liskov Substitution
khi P là parent của C, thì C nên làm đc những việc mà P làm dc. nếu k thỏa mãn dc điều này, ta k nên dùng P làm parent của C (có thể dùng cách khác như:  dùng class khác làm parent của C,...)
nói cách khác chuẩn hơn, nếu C là con của P, thì C có thể dùng để thay thế P ở mọi nơi trong chương trình mà vẫn chạy đúng.
ví dụ đúng: cha: class Personcon: class Baby, class Adult
tại sao phải tuân thủ Liskov? 
vì mọi dev đều mong đợi class con hoạt động giống class cha, nên nếu k tuân thủ thì code sẽ khó hiểu,
khi k tuân thủ, code có thể chạy sai ở runtime
nếu class con hoạt động khác class cha, khi khởi tạo class con sẽ làm thay đổi hành vi của class cha --> khó hiểu, khó bảo trì


Interface Segregation
nghĩa là: k nên ép 1 class phải triển khai những phương thức mà nó k sử dụng
nói cách khác, thay vì tạo 1 interface lớn, hãy chia thành nhiều interface riêng biệt để mỗi class chỉ cần implement những gì nó thực sự cần


Dependency Inversion
nghĩa là: high level module k nên phụ thuộc vào low level module, mà chúng nên phụ thuộc vào abstraction
ví dụ: https://www.figma.com/board/DiwrOCIBu6hmWp1i2C6jtJ/every-things?node-id=8068-2036&t=ySFhfKVLi8ic3E7f-11




# cách sử dụng SOLID
trong thực tế, SOLID k dc áp dụng 100%, vì k phải lúc nào cũng cần chúng,
áp lực về thời gian và chi phí,
yêu cầu thay đổi liên tục....


SOLID giúp code simple, nhưng cũng có thể làm code phức tạp. hãy dùng nó khôn ngoan