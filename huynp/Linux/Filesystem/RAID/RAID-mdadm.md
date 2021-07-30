# RAID
RAID (Redundant Arrays of Inexpensive Disks) là à một kỹ thuật ảo hóa, cho phép ghép nhiều ổ đĩa cứng vật lý thành một hệ thống bộ nhớ.
Mỗi một loại RAID kèm theo những tính năng như
- Gia tăng tốc độ đọc/ghi dữ liệu
- Độ an toàn cho dữ liệu được lưu trữ
- Dung lượng lưu trữ lớn
- Hiệu suất làm việc cao

## Các kỹ thuật trong RAID
- **Parity**: là một phương pháp tạo lại nội dung bị mất từ thông tin parity. Ứng dụng trong RAID5 và RAID6
- **Stripe**: phân phối dữ liệu ngẫu nhiên vào nhiều đĩa, như vậy sẽ không có dữ liệu đầy đủ trong một đĩa.
- **Mirroring**: tạo một bản sao của cùng một dữ liệu. Sử dụng trong RAID1 và RAID10
- **Hot spare**: là một ổ đĩa dự phòng trong máy chủ, có thể tự động thay thế và xây dựng lại các ổ đĩa bị lỗi.
- **Chunks**: là một kích thước của dữ liệu tối thiểu từ 4KB trở lên. Bằng cách xác định kích thước chunks mà có thể tăng hiệu suất I/O.

## Các chuẩn RAID
### RAID 0
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/9b/RAID_0.svg/800px-RAID_0.svg.png" alt="drawing" width="200"/>

- **Ưu điểm**: Striping, phân chia khối dữ liệu và trải chúng qua các ổ cứng. Tăng hiệu quả thực thi.
- **Nhược điểm**: tiềm ẩn rủi ro về dữ liệu, tỉ lệ mất dữ liệu càng cao khi càng có nhiều ổ cứng.

Cần tối thiểu 2 ổ. Phù hợp với những dữ liệu không quan trọng, nếu mất có thể không cần hoặc lấy lại được từ nơi khác. Nhưng loại RAID này không được khuyên dùng.
### RAID 1
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/b/b7/RAID_1.svg/800px-RAID_1.svg.png" alt="drawing" width="200"/>

- **Ưu điểm**: Mirroring đảm bảo an toàn hơn về dữ liệu do dữ liệu được ghi vào 2 ổ giống hệt nhau
- **Nhược điểm**: hiệu suất không cao và tốn kém chi phí do phải chia nửa bộ nhớ để sao lưu

Cần tối thiểu 2 ổ. Phù hợp với trường hợp không yêu cầu dung lượng lớn mà lại muốn đảm bảo 100% khôi phục.
### RAID 10
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/b/bb/RAID_10.svg/800px-RAID_10.svg.png" alt="drawing" width="400"/>

Kết hợp của RAID 1 và RAID 0 (RAID 1+0), làm cả hai công việc của Mirror và Striping.
- **Ưu điểm**: lưu trữ nhanh nhẹn và an toàn, vừa nâng cao hiệu suất mà lại đảm bảo dữ liệu không bị thất thoát khi một trong các ổ cứng bị hỏng
- **Nhược điểm**: chi phí cao

Cần tối thiểu 4 ổ và chỉ sử dụng 50% dung lượng (mirroring). Phù hợp cho database server hay những hệ thống yêu cầu tính sẵn sàng cao (high availability)

### RAID 5
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/6/64/RAID_5.svg/800px-RAID_5.svg.png" alt="drawing" width="400"/>

Hoạt động theo kỹ thuật Parity. Nếu một ổ cứng bị hỏng, dữ liệu được xây dựng lại dựa trên các thông tin đã được lưu trên các ổ đĩa tốt còn lại. Đảm bảo cho dữ liệu khi bất kì một ổ đĩa nào bị lỗi. 
- **Ưu điểm**: nâng cao hiệu suất, an toàn dữ liệu
- **Nhược điểm**: giá thành cao, hiệu quả thực thi giảm trong quá trình phục hồi

Cần tối thiểu 3 ổ, 2 ổ để striping, 1 ổ để phân phối parity.
- Phù hợp cho những fileserver, backup server, server lưu trữ,... đáp ứng hiệu suất phù hợp nhất với giá thành.
- Không phù hợp với database server vì RAID 5 không phù hợp với random write, bởi mỗi khi dữ liệu được nạp vào sẽ đồng nghĩa yêu cầu parity một lần cập nhật
### RAID 6
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/7/70/RAID_6.svg/1024px-RAID_6.svg.png" alt="drawing" width="500"/>

Hoạt động tương tự như RAID 5 nhưng với double Parity
- **Ưu điểm**: sử dụng trong mảng lớn với khả năng khôi phục lớn
- **Nhược điểm**: tốc độ, hiệu suất kém so với RAID 5

Cần tối thiểu 4 ổ để đáp ứng double parity. 

