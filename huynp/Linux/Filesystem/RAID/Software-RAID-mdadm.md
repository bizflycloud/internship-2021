## mdadm 
Là một công cụ dùng để quản lý RAID mềm trong hầu hết các bản phân phối Linux.

Các chế độ hoạt động:
- Assemble: kết hợp những mảng đã tạo thành mảng hoạt động
- Build: tạo một mảng mới không có superblock (là một khoảng được tạo trên mỗi thiết bị, chứa thông tin về thiết bị RAID và cho phép sửa chữa việc ghép mảng) 
- Create: tạo một mảng mới có superblock
- Monitor: theo dõi sự thay đổi của một hoặc nhiều thiết bị
- Grow: thay đổi kích thước mảng 
- Manage: quản lý các thiết bị như thêm mới hoặc xóa
- Misc: xóa các superblock cũ và thu thập dữ liệu
- Auto-detect: yêu cầu kernel Linux kích hoạt các mảng


Các option:
- `-C` tạo RAID mới.
- `-l` level của RAID.
- `-n` thiết bị dành RAID (là 2 phân vùng vừa tạo)
- `-E` kiểm tra thông tin

Tạo RAID:
Trước tiên cần phải phân vùng từ những ổ cứng, ví dụ với RAID 0 cần phải có ít nhất 2 ổ cứng.

Tạo RAID 0 từ 2 phân vùng vừa tạo và kiểm tra

    mdadm -C /dev/md0 -l raid0 -n 2 /dev/sd[b-c]1
    mdadm -E /dev/sd[b-c]1
