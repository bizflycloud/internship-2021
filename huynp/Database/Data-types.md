# Các kiểu dữ liệu số trong MySQL
## Kiểu dữ liệu số
TINYINT
- Độ dài 1 byte, giá trị có dấu 
  - SMALLINT, INT, MEDIUMINT, BIGINT
  - FLOAT, DOUBLE
  - DECIMAL
- Kiểu dữ liệu Data và Time
  - DATE (YYYY-MM-DD)
  - DATETIME (YYYY-MM-DD HH:MM:SS)
  - TIMESTAMP
  - TIME
  - YEAR(M)
- Kiểu dữ liệu chuỗi trong MySQL
  - CHAR: chiều dài chuỗi cố định, nhanh hơn so với VARCHAR
  - VARCHAR: chiều dài chuỗi thay đổi
  - BLOB, TINYBLOB, MEDIUMBLOB, LONGBLOB: chuỗi được lưu ở dạng nhị phân
  - TEXT, TINYTEXT, MEDIUMTEXT, LONGTEXT: tương đương với BLOB nhưng sử dụng bộ ký tự khác, thay vì là nhị phân của BLOB
  - ENUM
