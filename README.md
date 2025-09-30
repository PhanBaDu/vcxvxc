# TỔNG HỢP CHỨC NĂNG

_Dựa trên tài liệu yêu cầu KH-20_RO.MD - Chức năng xử lý đặt trước của Admin_

## MỤC LỤC

1. [Chức năng xử lý đặt trước](#1-chức-năng-xử-lý-đặt-trước)
   - 1.1 [Danh sách đơn hàng đặt trước](#11-danh-sách-đơn-hàng-đặt-trước)
   - 1.2 [Xem chi tiết đơn đặt trước](#12-xem-chi-tiết-đơn-đặt-trước)
   - 1.3 [Xử lý yêu cầu đặt trước](#13-xử-lý-yêu-cầu-đặt-trước)
   - 1.4 [Cập nhật trạng thái đặt trước](#14-cập-nhật-trạng-thái-đặt-trước)
   - 1.5 [Thông báo có hàng](#15-thông-báo-có-hàng)

---

## 1. CHỨC NĂNG XỬ LÝ ĐẶT TRƯỚC

### 1.1 DANH SÁCH ĐƠN HÀNG ĐẶT TRƯỚC

#### 1.1.1 Thông tin màn hình:

| Screen        | Danh sách đơn hàng đặt trước                         |
| ------------- | ---------------------------------------------------- |
| Description   | Hiển thị danh sách đơn đặt trước của khách hàng      |
| Screen Access | Admin truy cập /admin/pre-orders hoặc menu Đặt trước |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                        | Type       | Data                                                                | Description          |
| --------------------------- | ---------- | ------------------------------------------------------------------- | -------------------- |
| **Tiêu đề trang**           | Text       | Đơn hàng đặt trước                                                  | Tiêu đề chính        |
| **Bộ lọc trạng thái**       | Select     | Tất cả / Chờ xử lý / Đã xác nhận / Đang chuẩn bị / Đã giao / Đã hủy | Lọc theo trạng thái  |
| **Bộ lọc thời gian**        | Select     | Hôm nay / Tuần này / Tháng này / Tất cả                             | Lọc theo thời gian   |
| **Tìm kiếm**                | Input      | Tìm theo mã đặt trước / tên khách                                   | Tìm nhanh            |
| **Bảng danh sách**          | Table      | Mã, Khách hàng, Sản phẩm, SL, Giá dự kiến, Tiền cọc, Trạng thái,... | Bảng dữ liệu chính   |
| **Nút xem chi tiết**        | Button     | Xem chi tiết                                                        | Mở trang chi tiết    |
| **Nút cập nhật trạng thái** | Button     | Cập nhật trạng thái                                                 | Mở modal cập nhật    |
| **Phân trang**              | Pagination | Điều hướng trang                                                    | Điều hướng danh sách |

#### 1.1.3 Hành động và xử lý:

| Action Name                      | Description                                                         | Success                                                                | Failure                                                   |
| -------------------------------- | ------------------------------------------------------------------- | ---------------------------------------------------------------------- | --------------------------------------------------------- |
| **Hiển thị danh sách đặt trước** | Hiển thị đầy đủ các đơn đặt trước kèm bộ lọc, tìm kiếm, phân trang. | Danh sách hiển thị chính xác, lọc/tìm kiếm hoạt động, phân trang mượt. | Không tải được dữ liệu, lọc/tìm kiếm sai, phân trang lỗi. |
| **Xuất dữ liệu**                 | Cho phép xuất CSV/XLSX danh sách theo bộ lọc hiện tại.              | File xuất đúng dữ liệu, định dạng chuẩn.                               | Xuất lỗi hoặc dữ liệu không khớp bộ lọc.                  |

### 1.2 XEM CHI TIẾT ĐƠN ĐẶT TRƯỚC

#### 1.2.1 Thông tin màn hình:

| Screen        | Chi tiết đơn đặt trước                      |
| ------------- | ------------------------------------------- |
| Description   | Hiển thị đầy đủ thông tin một đơn đặt trước |
| Screen Access | Từ danh sách đặt trước, chọn Xem chi tiết   |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                        | Type      | Data                                            | Description                 |
| --------------------------- | --------- | ----------------------------------------------- | --------------------------- |
| **Thông tin cơ bản**        | Card      | Mã đặt trước, Ngày tạo, Trạng thái, Mức ưu tiên | Tổng quan yêu cầu           |
| **Khách hàng**              | Card      | Họ tên, SĐT, Email                              | Thông tin người đặt         |
| **Sản phẩm**                | Card List | Tên, SL, Giá dự kiến, Tổng, Tiền cọc, Còn lại   | Chi tiết sản phẩm đặt trước |
| **Địa chỉ giao hàng**       | Card      | Địa chỉ, Thành phố, Quận/Huyện, Phường/Xã       | Thông tin giao nhận         |
| **Phương thức thanh toán**  | Text      | COD / Banking / MoMo / ZaloPay / Viettel Money  | Phương thức đã chọn         |
| **Lịch sử xử lý**           | Timeline  | Thời gian, Hành động, Người xử lý, Ghi chú      | Theo dõi tiến trình         |
| **Nút cập nhật trạng thái** | Button    | Cập nhật trạng thái                             | Mở modal cập nhật           |
| **Nút gửi thông báo**       | Button    | Gửi thông báo                                   | Gửi thông báo đến khách     |

#### 1.2.3 Hành động và xử lý:

| Action Name                     | Description                                                               | Success                                       | Failure                                        |
| ------------------------------- | ------------------------------------------------------------------------- | --------------------------------------------- | ---------------------------------------------- |
| **Hiển thị chi tiết đặt trước** | Hiển thị đầy đủ thông tin đơn, lịch sử xử lý, cho phép thao tác cập nhật. | Thông tin đầy đủ, rõ ràng, số liệu chính xác. | Thiếu thông tin, sai số liệu, lỗi tải lịch sử. |
| **Thêm ghi chú xử lý**          | Admin thêm ghi chú nội bộ cho từng bước xử lý.                            | Ghi chú được lưu, hiện trong Timeline.        | Không lưu được ghi chú.                        |

### 1.3 XỬ LÝ YÊU CẦU ĐẶT TRƯỚC

#### 1.3.1 Thông tin màn hình:

| Screen        | Xử lý yêu cầu đặt trước                                    |
| ------------- | ---------------------------------------------------------- |
| Description   | Phản hồi khi sản phẩm đã có hàng nhưng chưa đăng công khai |
| Screen Access | Từ chi tiết đơn đặt trước                                  |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                   | Type   | Data                                           | Description               |
| ---------------------- | ------ | ---------------------------------------------- | ------------------------- |
| **Modal xử lý**        | Modal  | Trạng thái, Nhân viên phụ trách, Ghi chú       | Thao tác xử lý            |
| **Tồn kho khả dụng**   | Text   | Số lượng hiện có                               | Kiểm tra khả năng đáp ứng |
| **Đề xuất phương án**  | Select | Chờ thêm hàng / Giao 1 phần / Hủy theo yêu cầu | Phương án xử lý           |
| **Nút xác nhận xử lý** | Button | Xác nhận                                       | Ghi nhận xử lý            |

#### 1.3.3 Hành động và xử lý:

| Action Name                | Description                                                        | Success                                      | Failure                                    |
| -------------------------- | ------------------------------------------------------------------ | -------------------------------------------- | ------------------------------------------ |
| **Kiểm tra tồn kho**       | Đối chiếu tồn kho trước khi phản hồi.                              | Số liệu tồn kho chính xác, hiển thị rõ ràng. | Không đọc được tồn kho, sai số liệu.       |
| **Gửi phản hồi cho khách** | Gửi thông báo (email/push) kèm phương án xử lý, thời gian dự kiến. | Thông báo gửi thành công, khách nhận được.   | Thông báo không gửi được/khách không nhận. |

### 1.4 CẬP NHẬT TRẠNG THÁI ĐẶT TRƯỚC

#### 1.4.1 Thông tin màn hình:

| Screen        | Cập nhật trạng thái đặt trước                           |
| ------------- | ------------------------------------------------------- |
| Description   | Thay đổi trạng thái: Chờ xử lý → ... → Đã giao / Đã hủy |
| Screen Access | Từ danh sách/chi tiết đặt trước                         |

#### 1.4.2 Chi tiết thành phần màn hình:

| Item                        | Type   | Data                                                       | Description           |
| --------------------------- | ------ | ---------------------------------------------------------- | --------------------- |
| **Modal trạng thái**        | Modal  | Trạng thái mới, Người xử lý, Ghi chú                       | Xác nhận thay đổi     |
| **Bảng quy ước trạng thái** | Card   | Chờ xử lý / Đã xác nhận / Đang chuẩn bị / Đã giao / Đã hủy | Quy ước chuẩn         |
| **Thông báo khách hàng**    | Toggle | Gửi thông báo khi thay đổi                                 | Bật/tắt gửi thông báo |

#### 1.4.3 Hành động và xử lý:

| Action Name            | Description                                                       | Success                                                              | Failure                                    |
| ---------------------- | ----------------------------------------------------------------- | -------------------------------------------------------------------- | ------------------------------------------ |
| **Đổi trạng thái đơn** | Cập nhật trạng thái theo tiến trình xử lý, ghi nhận vào Timeline. | Trạng thái cập nhật đúng, Timeline bổ sung bản ghi.                  | Không cập nhật được, thiếu log.            |
| **Khóa/hủy đơn**       | Hủy đơn khi khách yêu cầu hoặc không còn khả năng đáp ứng.        | Trạng thái chuyển Đã hủy, hoàn tất thông báo và quy trình liên quan. | Trạng thái/hoàn tiền/thông báo không khớp. |

### 1.5 THÔNG BÁO CÓ HÀNG

#### 1.5.1 Thông tin màn hình:

| Screen        | Thông báo có hàng                                     |
| ------------- | ----------------------------------------------------- |
| Description   | Gửi thông báo đến khách đã đặt trước khi hàng về      |
| Screen Access | Từ chi tiết đặt trước hoặc module Thông báo của Admin |

#### 1.5.2 Chi tiết thành phần màn hình:

| Item                  | Type   | Data                                        | Description             |
| --------------------- | ------ | ------------------------------------------- | ----------------------- |
| **Mẫu thông báo**     | Form   | Tiêu đề, Nội dung, Sản phẩm, Giá, Thời gian | Soạn nội dung thông báo |
| **Kênh gửi**          | Select | Email / Push / SMS                          | Chọn kênh gửi           |
| **Đối tượng nhận**    | Select | Theo đơn đặt trước / Theo sản phẩm          | Chọn nhóm người nhận    |
| **Nút gửi thông báo** | Button | Gửi thông báo                               | Thực hiện gửi           |

#### 1.5.3 Hành động và xử lý:

| Action Name               | Description                                                    | Success                                           | Failure                                     |
| ------------------------- | -------------------------------------------------------------- | ------------------------------------------------- | ------------------------------------------- |
| **Gửi thông báo có hàng** | Gửi thông báo cho khách đã đặt trước hoặc đã đăng ký quan tâm. | Thông báo gửi đúng đối tượng, nội dung chính xác. | Không gửi được, gửi sai nhóm, nội dung lỗi. |
| **Theo dõi tỉ lệ mở**     | Ghi nhận tỉ lệ mở/ràng buộc theo kênh để tối ưu chiến dịch.    | Số liệu hiển thị chính xác, hỗ trợ xuất báo cáo.  | Không ghi nhận được số liệu.                |
