
# sp iu
data trong src gồm 2 loại row: row có id dùng để update, row k có id dùng để insert
khi insertupdate vào bảng XDetail, thì phải check để đảm bảo mỗi row X chỉ có duy nhất 1 row XDetail
thứ tự thông thường là delete - update - insert
UPDATE đi chung với inner join
insert đi cùng left join
trong sql query, mqh dest-src rất phổ biến





# các câu sql thông dụng cần thuộc lòng
-  SELECT VALUE FROM STRING_SPLIT(''' + @iv_SKU + ''', '';'') --> select các sku bị cắt từ chuỗi sku
- cú pháp: = Case WHEN THEN
-  ISNULL(expression, replacement_value)
khi expression != null, nó trả về expression
khi expression = null, nó trả về replacement_value

insert into x (...) select ... from y,
select bao nhiêu insert bấy nhiêu

# nguyên tắc dùng các keyword
Mỗi từ khóa trong SQL có nguyên tắc sử dụng rất nghiêm ngặt và thường chỉ dùng cho một số công việc cụ thể.
nguyên tắc dùng GROUP BY
trong câu SELECT, các cột k thuộc hàm tổng hợp thì bắt buộc phải có trong GroupBy
- chỉ dùng trong câu SELECT
- các cột trong SELECT phải có trong GROUP BY, (trừ khi dùng với COUNT, SUM, AVG)


#
Transaction
là 1 nhóm các thao tác trên db
dùng “begin transaction” để dùng nó
các thao tác trong transation chỉ dc commit khi tất cả thao tác đó thành công,

 Aggregate Function
thường đi cùng với GROUP BY
các hàm tổng hợp phổ biến: SUM, AVG,...
(vd: sp [plm].[usp_iu_SampleRequest])

- link học
https://www.youtube.com/watch?v=jcoJuc5e3RE

- với cú pháp sql, chỉ cần nói "làm gì", k cần nói "làm thế nào"

diff innerjoin và leftjoin
innerjoin chỉ lấy phần giao, left join lấy phần hợp

 khi dùng “SELECT  p.SKU, p.Name” thì cột sẽ là SKU/Name

tại sao khi insert/update hay dùng join? vì join giúp xác định dữ liệu cần cập nhật (tức xác định các cặp row tương ứng trong 2 bảng)
