# Learn-SQL

## Các câu hỏi thường gặp về SQL

### 1. SQL là gì:

Viết tắt của Structured Query Language - ngôn ngữ truy vấn cấu trúc.  Nó được thiết kế để quản lý dữ liệu trong một hệ thống quản lý cơ sở dữ liệu quan hệ (RDBMS). SQL là ngôn ngữ cơ sở dữ liệu, được dùng để tạo, xóa, lấy các hàng và sửa đổi các hàng.

### 2. Định nghĩa JOIN và các loại JOIN

Từ khóa JOIN được dùng để nạp dữ liệu từ 2 hay nhiều bảng liên quan. Sử dụng từ khóa JOIN khi cần truy vấn các cột dữ liệu từ nhiều bảng khác nhau để trả về trong cùng một tập kết quả.  
Các loại JOIN:

- **INNER JOIN**  
    
    - Lấy các bản ghi trùng khớp ở cả hai bảng (theo điều kiện JOIN). Nếu không có giá trị trùng khớp, dòng đó sẽ không xuât hiện.
    - Đặc điểm: 
        - Là loại JOIN phổ biến nhất.
        - Bỏ qua các bản ghi không có tương ứng ở bảng còn lại.
    - Chỉ nên dùng khi chỉ quan tâm đến dữ liệu khớp nhau giữa các bảng.

- **LEFT OUTER JOIN**

    - Lấy toàn bộ bản ghi từ bảng bên trái, và các bản ghi khớp ở bảng bên phải (Nếu không có thì **NULL**).
    - Đặc điểm:
        - Giữ lại dữ liệu bên trái, kể cả khi không khớp.
        - Phù hợp khi cần tất cả dữ liệu từ bảng chính và thêm thông tin bổ sung (Nếu có).
    - Nếu bên phải không có khớp, các cột của bảng đó sẽ là **NULL**

- **RIGHT OUTER JOIN**

    - Ngược lại với LEFT JOIN.

- **FULL OUTER JOIN**

    - Kết hợp cả LEFT và RIGHT JOIN - lấy tất cả bản ghi từ cả hai bảng, ghép nếu có khớp, nếu không thì điền **NULL**.
    - Đặc điểm:
        - Lưu giữ toàn bọ giữ liệu, kể cả không khớp.
        - Không được hỗ trợ bởi một số hệ quản trị (MySQL không hỗ trợ trực tiếp mà phải mô phỏng bằng UNION).

- **CROSS JOIN**

    - Lấy tích Descartes của hai bảng - mỗi bản ghi của bảng A sẽ kết hợp với tất cả bản ghi của bảng B.
    - Đặc điểm:
        - Không có điều kiện **ON**.
        - Dùng khi muốn tạo tổ hợp tất cả các cặp dữ liệu có thể.
    - Cẩn thận khi bảng lớn.

- **SELF JOIN**

    - JOIN một bảng với chính nó - hữu ích khi có quan hệ phân cấp.
    - Đặc điểm:
        - Phải dùng alias để phân biệt.
        - Dễ dùng trong cấu trúc cây.

### 3. CHECK Constraint

Một ràng buộc CHECK được sử dụng để giới hạn các giá trị hoặc loại dữ liệu có thể được lưu trữ trong một cột. Nếu bản ghi không đáp ứng thì không được lưu trữ vào bảng.

### 4. BOOLEAN

Đối với trường dữ liệu BOOLEAN, có 2 giá trị: -1 (TRUE), 0 (FALSE).

### 5. DML & DDL

- **DML**: Ngôn ngữ thao tác dữ liệu (Data Manipulation Language) -> INSERT, UPDATE, DELETE.
- **DDL**: Ngôn ngữ định nghĩa dữ liệu (Data Definition Language) -> CREATE, ALTER, DROP, RENAME.

### 6. Thứ tự của SQL SELECT

- Thứ tự các mệnh đề SQL SELECT là: SELECT -> FROM -> WHERE -> GROUP BY -> HAVING -> ORDER BY.

### 7. Sự khác biệt giữa các lệnh TRUNCATE, DELETE và DROP

- **DELETE**: xóa một hoặc tất cả các hàng từ một bảng dựa trên điều kiện và có thể phục hồi.
- **TRUNCATE**: xóa tất cả các hàng từ một bảng bằng cách phân bổ các trang bộ nhớ và không thể phục hồi.
- **DROP**: xóa hoàn toàn một bảng từ cơ sở dữ liệu.

### 8. Các thuộc tính của một giao dịch

- Được gọi là **ACID**, bao gồm:
    - Atomicity: Tính nguyên tử.
    - Consistency: Tính nhất quán.
    - Isolation: Cô lập.
    - Durability: Độ bền.

### 9. Xác định UNION, MINUS, UNION ALL, INTERSECT?

Là các set operations (phép toán tập hợp), thường dùng để kết hợp hoặc so sánh kết qua của nhiều câu truy vấn SELECT.

- **UNION**:
    - Kết hợp của hai hoặc nhiều câu lệnh SELECT, loại bỏ các bản ghi trùng lặp.
    - Đặc điểm:
        - Trả về tập hợp duy nhất của các bản ghi.
        - Các cột của các truy vấn con phải có số lượng và kiểu dữ liệu tương ứng.
    - Lưu ý: Có thể tốn tài nguyên vì loại bỏ bản ghi trùng.
- **UNION ALL**:
    - Tương tự như UNION nhưng giữ lại các bản ghi trùng lặp.
    - Đặc điểm:
        - Hiệu suất nhanh hơn UNION vì không thực hiện lọc trùng.
        - Dùng khi cần đầy đủ dữ liệu, bao gồm cả bản ghi giống nhau.
- **INTERSECT**:
    - Trả về bản ghi chung giữa hai tập kết quả SELECT.
    - Đặc điểm:
        - Tương đương phép giao trong toán học.
        - Chỉ giữ những bản ghi có mặt ở cả hai câu truy vấn.
    - Không hỗ trợ trực tiếp trong một số hệ quản trị như MySQL (có thể giả lập bằng INNER JOIN).
- **MINUS** (hoặc **EXCEPT** trong một số hệ):
    - Trả về bản ghi từ câu truy vấn đầu tiên không xuất hiện trong truy vấn thứ hai.
    - Đặc điểm:
        - Là phép hiệu trong tập hợp: A - B.
        - Giúp tìm ra phần không trùng khớp.
    - Lưu ý:
        - Oracle dùng MINUS.
        - PostgreSQL, SQL Server dùng EXCEPT.
        - MySQL không hỗ trợ trực tiếp - phải mô phỏng bằng `LEFT JOIN ... WHERE ... IS NULL.`

### 10. Sự khác biệt của WHERE và HAVING?

Cả hai mệnh đề đều chỉ định điều kiện tìm kiếm nhưng mệnh đề Having chỉ được sử dụng với câu lệnh SELECT và thường được sử dụng với mệnh đề GROUP BY. Nếu không có mệnh đề GROUP BY thì Having sử dụng giống mệnh đề WHERE.

## Kiến thức tối ưu / quan trọng

### 1. Index trong SQL

- Khái niệm: Index là cấu trúc dữ liệu giúp tăng tốc truy vấn bằng cách giảm số dòng phải quét trong bảng.
- Các loại Index phổ biến:
    - **B-Tree Index**: Mặc định trong hầu hết các DBMS (MySQL, PostgreSQL). Tốt cho so sánh: `=`, `>`, `<`, `BETWEEN`.
    - **Hash Index**: Nhanh cho `=`, nhưng không hỗ trợ cho range(`<`, `>`). Dùng trong memory engine.
    - **Full-text Index**: Hỗ trợ tìm kiếm văn bản (natural language).
    - **Composite Index**: Chỉ mục kết hợp nhiều cột. Rất mạnh nhưng cần lưu ý thứ tự cột.
    - **Unique Index**: Đảm bảo giá trị duy nhất.
    - **Bitmap Index**: Tốt cho dữ liệu ít giá trị khác nhau (low-cardinality).
- Cách hoạt động:
    - Duyệt theo **cây B-Tree** để tìm giá trị.
    - Nếu có index phù hợp, DBMS sẽ dùng index scan thay vì full table scan.
    - Index không phù hợp thì hệ thống bỏ qua.
- Lưu ý:
    - INSERT hoặc UPDATE nhiều: index có thể làm chậm do phải cập nhật.
    - Không nên tạo quá nhiều index - chi phí bảo trì cao.
    - Dùng `EXPLAIN` để biết có dùng index hay không.
- Khi nào nên sử dụng Index?  
Có một số quy luật thường thấy khi chọn một cột (hoặc tập các cột) để tạo index:
    1. **Khóa và các cột có giá trị độc nhất (unique)**: Database thường sẽ tự động tạo index cho các cột này nên để tránh việc trùng lặp và tiêu tốn bộ nhớ, ta không nên tạo thêm index cho chúng.
    2. **Tần suất được sử dụng**: Khi tần suất sử dụng câu truy vấn càng lớn thì việc tạo index sẽ giúp làm giảm càng nhiều thời gian truy vấn.
    3. **Số lượng bản ghi của bảng**: Số lượng bảng ghi của bảng càng nhiều thì tốc độ truy vấn sẽ càng giảm, lợi thế của việc sử dụng index trên các bảng này lại càng rõ ràng so với những bảng có số lượng bản ghi ít.
    4. **Dữ liệu của bảng tăng trưởng nhanh**: Index sẽ tự động cập nhật khi có một bản ghi được thêm vào cơ sở dữ liệu, vì vậy khi đánh chỉ mục cho 1 bảng nó sẽ làm chậm lại các hành động thêm sửa xóa bản ghi. Vậy nên một bảng thường xuyên được cập nhật nên có ít index hơn một bảng hiếm khi cập nhật.
    5. **Không gian bộ nhớ**: Khi tạo index sẽ sử dụng chính không gian bộ nhớ của cơ sở dữ liệu nên khi cơ sở dữ liệu có kích thước lớn ta cần lựa chọn cẩn thận trường nào sẽ sử dụng làm index.
    6. **Dữ liệu có đa dạng giá trị**: Index được tạo dựa trên các giá trị trong cột mà nó trỏ tới.
- Cách tạo index trong **PostgreSQL**:

    `CREATE INDEX index_name ON table_name (COLUMN1, COLUMN2,...)`