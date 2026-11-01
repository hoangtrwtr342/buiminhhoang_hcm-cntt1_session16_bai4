# Bài 4 : Tối ưu hóa Lưu trữ Dữ liệu Doanh nghiệp


## 1. Giải pháp kỹ thuật
1. Thiết lập Files On-Demand:

  1. OneDrive: Vào Settings > Sync and backup > bật Files On-Demand. Chuột phải vào thư mục video trong File Explorer chọn Free up space (icon chuyển sang hình đám mây, dung lượng thực tế trên máy về 0 bytes).
  
  2. Google Drive: Vào Settings > Preferences > chọn Stream files (chỉ tải tạm khi mở, không tải toàn bộ file về máy).
  
  3. Xử lý bẫy nghẽn mạng & gián đoạn:
  
  4. Tránh nghẽn mạng: Giới hạn tốc độ tải lên (Upload Rate limit) ở mức 20–30% trong cài đặt đồng bộ, hoặc hẹn giờ đồng bộ vào ban đêm (00:00 – 06:00).
  
  5. Tránh đứt đoạn khi gập máy: Trong Windows Power Options, chỉnh When I close the lid thành Do nothing khi cắm sạc. Tận dụng cơ chế Resumable Upload sẵn có của Cloud để tự nối tiếp quá trình tải khi có mạng trở lại.

## 2. Báo cáo dung lượng & Chứng minh hiệu quả
Thông số hệ thống:
  
  Dung lượng SSD Laptop: 256 GB (khả dụng thực tế khoảng 130 GB sau khi trừ hệ điều hành và phần mềm).
  
  Dữ liệu Cloud: 500 GB (gấp ~3.85 lần dung lượng trống thực tế).
  
  Chứng minh hiệu quả (Trước vs Sau):
  
  Trước khi áp dụng (Full Sync): Máy cố tải toàn bộ 500 GB dẫn đến tràn ổ SSD (báo lỗi Disk Full), treo hệ thống và ngừng đồng bộ.
  
  Sau khi áp dụng (Files On-Demand): Kích thước hiển thị vẫn là 500 GB nhưng dung lượng chiếm dụng thật trên SSD chỉ khoảng 50 – 100 MB (chỉ lưu metadata và thumbnail).
  
  Bộ nhớ khả dụng: Giữ nguyên mức an toàn ~130 GB trống. Khi cần xem một video 2 GB, hệ thống chỉ tạm thời tải đúng 2 GB đó vào bộ nhớ đệm cache rồi tự động giải phóng.
  
  Quản lý vòng đời dữ liệu (Data Lifecycle):
  
  Bật Storage Sense trên Windows để tự động dọn dẹp và đưa các file video không dùng sau 14–30 ngày về lại trạng thái Online-only.
  
  Phân tầng dữ liệu cũ (> 90 ngày) sang bộ nhớ lưu trữ lạnh (Cold Storage) để tối ưu chi phí Cloud.
