
#HCMUS 
#PostgreSQL
#MongoDB


# Thông tin kì thi

Phòng thi: E404 (NVC)
Thời gian: 10/07/2024 - 13h30


# 1. Tổng quan về Cơ sở Dữ liệu (Database)

#ER-Model
#Database

![[Pasted image 20240706172458.png]]

Dữ liệu --> Thông tin --> Tri thức --> Quyết định -->| Dữ liệu

![[Pasted image 20240706172606.png]]

![[Pasted image 20240706172633.png]]


**Cơ sở dữ liệu** (Database - DB) là tập hợp có tổ chức của các dữ liệu được lưu trữ

![[Pasted image 20240706172811.png]]

**Hệ quản trị cơ sở dữ liệu** (Database Management System - DBMS) là hệ thống phần mềm giúp người dùng thực hiện các thao tác với CSDL

![[Pasted image 20240706172910.png]]

## 1.1. Mô hình thực thể kết hợp - ER Model

**Entity-relationship model (ER Model)** là mô hình biểu diễn mối quan hệ giữa các thực thể khác nhau
- Gồm các loại **thực thể (entity)**, các **thuộc tính (attribute)** và các mối **quan hệ (relationship)**
- Có thể được biểu diễn bằng các sơ đồ thực thể kết hợp (Entity-relationship diagram - ERD)
Bằng việc sử dụng mô hình ER, có thể dễ dàng đặc tả được mối quan hệ giữa các thực thể ngòai đời thực, từ đó thiết kế các CSDL quan hệ phù hợp để lưu trữ dữ liệu

![[Pasted image 20240706173335.png]]

![[Pasted image 20240706173353.png]]


## 1.2. Mô hình dữ liệu quan hệ

Bảng (relation) tương đương với mỗi hình chữ nhật (entity) trong ERD (Entity
Relationship Datagram).
- Trong mỗi bảng sẽ có nhiều cột (column/attribute). Các cột này tương đương với hình oval (cũng gọi là attribute) trong ERD.
- Mỗi dòng (tuple/record/row) trong một bảng theo lý thuyết phải có giá trị unique.(nhưng trong thực tế nó có thể bị lặp lại do sai sót)

![[Pasted image 20240706174009.png]]

**Primary key**: Mỗi bảng có một cột Primary Key. Đây là cột để định danh duy nhất
mỗi record trong table của cơ sở dữ liệu, cột này không được chứa null value

**Foreign key**: là cột được ghi chú (FK) ở bảng này, và là cột Primary Key ở bảng khác. Dùng để kết nối bảng này với bảng khác - là khái niệm cốt lõi của Relational database.

Ví dụ: ![[Pasted image 20240706174201.png]]

## 1.3. Tại sao database quan trọng

1. Easier to manage data
2. Improved data sharing
3. Improved data security
4. Better enforce data quantity


# 2. PostgreSQL

#PostgreSQL 

![[NoiDungOnThi.jpg]]
## 2.1. Thao tác với Database

Các thao tác thường gặp với cơ sở dữ liệu (database) trong PostgreSQL bao gồm quản lý cơ sở dữ liệu, bảng, và các thành phần liên quan. Dưới đây là một số thao tác phổ biến:

### 1. **Tạo và Xóa Cơ Sở Dữ Liệu**

**Tạo cơ sở dữ liệu:**

```sql
CREATE DATABASE database_name;
```

**Xóa cơ sở dữ liệu:**

```sql
DROP DATABASE database_name;
```

### 2. **Kết Nối và Ngắt Kết Nối với Cơ Sở Dữ Liệu**

**Kết nối với cơ sở dữ liệu:**

```sql
\c database_name;
```

**Ngắt kết nối với cơ sở dữ liệu:**

```sql
\q
```

### 3. **Tạo và Xóa Bảng**

**Tạo bảng:**

```sql
CREATE TABLE table_name (
    column1 datatype PRIMARY KEY,
    column2 datatype,
    column3 datatype
);
```

**Xóa bảng:**

```sql
DROP TABLE table_name;
```

### 4. **Thêm, Cập Nhật và Xóa Cột**

**Thêm cột:**

```sql
ALTER TABLE table_name
ADD COLUMN column_name datatype;
```

**Cập nhật cột:**

```sql
ALTER TABLE table_name
ALTER COLUMN column_name SET DATA TYPE new_datatype;
```

**Xóa cột:**

```sql
ALTER TABLE table_name
DROP COLUMN column_name;
```

### 5. **Thêm, Cập Nhật và Xóa Index**

**Thêm index:**

```sql
CREATE INDEX index_name
ON table_name (column_name);
```

**Xóa index:**

```sql
DROP INDEX index_name;
```

### 6. **Quản Lý Người Dùng và Quyền**

**Tạo người dùng:**

```sql
CREATE USER username WITH PASSWORD 'password';
```

**Gán quyền cho người dùng:**

```sql
GRANT privilege_name ON database_name TO username;
```

**Thu hồi quyền từ người dùng:**

```sql
REVOKE privilege_name ON database_name FROM username;
```

**Xóa người dùng:**

```sql
DROP USER username;
```

### 7. **Sao Lưu và Phục Hồi Dữ Liệu**

**Sao lưu dữ liệu:**

```sh
pg_dump database_name > backup_file.sql
```

**Phục hồi dữ liệu:**

```sh
psql database_name < backup_file.sql
```

### 8. **Tạo và Quản Lý Khóa Ngoại (Foreign Key)**

**Tạo khóa ngoại:**

```sql
ALTER TABLE child_table
ADD CONSTRAINT fk_name
FOREIGN KEY (column_name)
REFERENCES parent_table (column_name);
```

**Xóa khóa ngoại:**

```sql
ALTER TABLE child_table
DROP CONSTRAINT fk_name;
```

## 2.2. Thiết kế Database

**Bước 1: Xác định mục đích lưu trữ dữ liệu.**

Ví dụ: Dữ liệu lưu trữ giao dịch của khách hàng

**Bước 2: Liệt kê các thông tin dữ liệu lưu trữ theo dạng "đối tượng" (objects): **

Ví dụ: Product, Customer, Payment method, ...

**Bước 3: Liệt kê và xác định các thuộc tính (attributes) của đối tượng. **

Ví dụ: 
1. Product: tên sản phẩm, khối lượng, giá,..., 
2. Customer: họ, tên, email, ...
3. ....

**Bước 4: Xác định xem mối quan hệ giữa các bảng là gì (One-One, One-Many, Many-One, Many-Many)**

Ví dụ: "Một sản phẩm có nhiều người bán", "Một sản phẩm có nhiều khách hàng", ...

**Bước 5: Lựa chọn mã định danh (ID) - thường là primary key**

Ví dụ:
1. Product: product_id
2. Customer: customer_id
3. ...

**Bước 6: Liên kết các bảng bằng các ID - xây dựng khóa ngoại**


## 2.3. CRUD

CRUD là viết tắt của các thao tác cơ bản trong cơ sở dữ liệu: Create (Tạo), Read (Đọc), Update (Cập nhật), và Delete (Xóa). Dưới đây là cách thực hiện các thao tác CRUD trong PostgreSQL:

### 1. **Create (Tạo)**

Để thêm dữ liệu mới vào bảng, chúng ta sử dụng câu lệnh `INSERT INTO`.

**Cú pháp:**

```sql
INSERT INTO table_name (column1, column2, ...)
VALUES (value1, value2, ...);
```

**Ví dụ:**

Giả sử bạn có một bảng tên là `employees` với các cột `id`, `name`, và `position`. Để thêm một nhân viên mới, bạn sử dụng:

```sql
INSERT INTO employees (id, name, position)
VALUES (1, 'John Doe', 'Software Engineer');
```

### 2. **Read (Đọc)**

Để đọc dữ liệu từ bảng, chúng ta sử dụng câu lệnh `SELECT`.

**Cú pháp:**

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

**Ví dụ:**

Để đọc tất cả các dữ liệu từ bảng `employees`:

```sql
SELECT * FROM employees;
```

Để đọc các dữ liệu cụ thể:

```sql
SELECT name, position FROM employees WHERE id = 1;
```

### 3. **Update (Cập nhật)**

Để cập nhật dữ liệu trong bảng, chúng ta sử dụng câu lệnh `UPDATE`.

**Cú pháp:**

```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

**Ví dụ:**

Để cập nhật vị trí công việc của nhân viên có `id` là 1:

```sql
UPDATE employees
SET position = 'Senior Software Engineer'
WHERE id = 1;
```

### 4. **Delete (Xóa)**

Để xóa dữ liệu khỏi bảng, chúng ta sử dụng câu lệnh `DELETE`.

**Cú pháp:**

```sql
DELETE FROM table_name
WHERE condition;
```

**Ví dụ:**

Để xóa nhân viên có `id` là 1:

```sql
DELETE FROM employees
WHERE id = 1;
```

## 2.4. Data Types

Trong PostgreSQL, có nhiều loại dữ liệu (data types) được sử dụng để lưu trữ các loại thông tin khác nhau. Dưới đây là các loại dữ liệu phổ biến:

### 1. **Số nguyên (Integer Types)**

- `smallint`: Số nguyên nhỏ, từ -32,768 đến 32,767.
- `integer` hoặc `int`: Số nguyên, từ -2,147,483,648 đến 2,147,483,647.
- `bigint`: Số nguyên lớn, từ -9,223,372,036,854,775,808 đến 9,223,372,036,854,775,807.
- `serial` và `bigserial`: Tự động tăng số nguyên (auto-incrementing).

### 2. **Số thực (Floating-Point Types)**

- `real`: Số thực với độ chính xác đơn (single precision).
- `double precision`: Số thực với độ chính xác kép (double precision).
- `numeric` hoặc `decimal`: Số thập phân với độ chính xác tùy ý (arbitrary precision).

### 3. **Ký tự (Character Types)**

- `char(n)`: Chuỗi ký tự cố định độ dài.
- `varchar(n)`: Chuỗi ký tự biến đổi độ dài với giới hạn.
- `text`: Chuỗi ký tự biến đổi độ dài không giới hạn.

### 4. **Boolean**

- `boolean`: Giá trị logic đúng (TRUE) hoặc sai (FALSE).

### 5. **Ngày và giờ (Date/Time Types)**

- `date`: Ngày (không có thời gian).
- `time [ (p) ] [ without time zone ]`: Thời gian trong ngày (không có múi giờ).
- `time [ (p) ] with time zone`: Thời gian trong ngày (có múi giờ).
- `timestamp [ (p) ] [ without time zone ]`: Ngày và giờ (không có múi giờ).
- `timestamp [ (p) ] with time zone`: Ngày và giờ (có múi giờ).
- `interval`: Khoảng thời gian.

### 6. **Dữ liệu kiểu hình học (Geometric Types)**

- `point`: Điểm (x, y).
- `line`: Đường vô hạn.
- `lseg`: Đoạn thẳng.
- `box`: Hình hộp chữ nhật.
- `path`: Đường dẫn.
- `polygon`: Đa giác.
- `circle`: Hình tròn.

### 7. **Dữ liệu kiểu mạng (Network Address Types)**

- `cidr`: Khối địa chỉ IP.
- `inet`: Địa chỉ IP.
- `macaddr`: Địa chỉ MAC.

### 8. **Dữ liệu kiểu bit (Bit String Types)**

- `bit [ (n) ]`: Chuỗi bit cố định độ dài.
- `bit varying [ (n) ]`: Chuỗi bit biến đổi độ dài.

### 9. **Dữ liệu kiểu tiền tệ (Monetary Types)**

- `money`: Số tiền tệ.

### 10. **Dữ liệu kiểu mảng (Array Types)**

- `type[]`: Mảng của bất kỳ loại dữ liệu nào.

### 11. **Dữ liệu kiểu JSON (JSON Types)**

- `json`: Dữ liệu JSON.
- `jsonb`: Dữ liệu JSON nhị phân (binary).

### 12. **Dữ liệu kiểu XML (XML Type)**

- `xml`: Dữ liệu XML.

### 13. **Dữ liệu kiểu UUID (UUID Type)**

- `uuid`: Định danh duy nhất toàn cầu.

### 14. **Dữ liệu kiểu HSTORE (HSTORE Type)**

- `hstore`: Cặp key-value.

### 15. **Dữ liệu kiểu composite (Composite Types)**

- Composite type là kiểu dữ liệu được tạo từ các kiểu dữ liệu khác.

### 16. **Dữ liệu kiểu phạm vi (Range Types)**

- `int4range`: Phạm vi số nguyên 32-bit.
- `int8range`: Phạm vi số nguyên 64-bit.
- `numrange`: Phạm vi số thực.
- `tsrange`: Phạm vi timestamp không có múi giờ.
- `tstzrange`: Phạm vi timestamp có múi giờ.
- `daterange`: Phạm vi ngày.

### Ví dụ sử dụng các loại dữ liệu

```sql
CREATE TABLE example (
    id serial PRIMARY KEY,
    name varchar(100),
    age integer,
    salary numeric(10, 2),
    is_active boolean,
    created_at timestamp with time zone,
    data jsonb
);
```
