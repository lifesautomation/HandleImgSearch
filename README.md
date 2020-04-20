>> Author: Lâm Thành Nhân\
>> Email: ltnhan.st.94@gmail.com
# ImageSearch Inactive (Background) Window cho AutoIt
> UDF HandleImgSearch.au3 sử dụng với mục đích tìm ảnh trong Handle của cửa sổ (cửa sổ không cần active). Cải tiến từ UDF ImageSearchEX.au3 và ImageSearchDLL.au3 (không phụ thuộc vào file .dll).\
> UDF này được tổng hợp và bổ sung từ nhiều nguồn, đầu mỗi Func sưu tầm mình đều giữ lại thông tin tác giả.
### Ưu điểm:
    - Rất nhanh (tích hợp ImageSearchDll ngay trong UDF).
    - Hỗ trợ Tolerance (Sai số màu sắc) và MaxImg (Tìm nhiều ảnh cùng lúc).
    - Tối ưu tốt, không leak memory.
    - Tìm kiếm qua Handle cửa sổ hoặc toàn màn hình dễ dàng.
    - Hỗ trợ global function (Sử dụng được nhiều hàm xử lý với 1 lần chụp).
    - Có ví dụ kèm theo cho từng hàm.
### Nhược điểm:
    - Tốc độ tìm nhiều ảnh sẽ chậm hơn BmpSearch đôi chút (Có Branch BmpSearch kèm theo).
    - Chỉ hỗ trợ compile AutoIt 32bit (chạy được trên Windows 64bit).

### Hàm global:
    _GlobalImgInit
    _GlobalImgCapture
    _GlobalGetBitmap
    _GlobalImgSearchRandom
    _GlobalImgSearch
    _GlobalGetPixel
    _GlobalPixelCompare
### Hàm Handle:
    _HandleImgSearch
    _BmpImgSearch
    _HandleGetPixel
    _HandlePixelCompare
    _HandleCapture

### Cách sử dụng và ví dụ: 
    Chú thích đầu mỗi hàm trong HandleImgSearch.au3 và vi dụ cụ thể có trong Example.au3.
### Lưu ý: 
    - Ảnh để tìm kiếm nên lưu dạng "24-bit Bitmap".
    - Trong hàm _GlobalImgInit và _HandleCapture đều có tham số $IsUser32. Với cách kiểm tra của mình thì True sẽ sử 
    dụng tốt hơn khi làm việc với cửa sổ của Explorer, False sẽ làm việc tốt hơn với các giả lập. Tuỳ mọi người kiểm 
    tra và sử dụng.
### Phiên bản khác: [Branch BmpSearch](https://github.com/ltnhanst94/AutoIt_HandleImgSearch/tree/BmpSearch): 
    - Sử dụng UDF BmpSeach (Không hỗ trợ Tolerance, hỗ trợ trả về nhiều vị trí nếu ảnh xuất hiện nhiều lần).
### Cập nhật:
    - 12/02/2020:
      + Bổ sung Param $MaxImg: Số kết quả trả về tối đa nếu có nhiều ảnh trùng nhau (Có thể tốc độ thực thi không 
      nhanh bằng BmpSearch vì hoàn toàn sử dụng vòng lặp của AutoIt).
      + Nếu $Hwnd = "" (Param của một số hàm) sẽ sử dụng ảnh màn hình hiện tại để chụp hoặc tìm kiếm.
      + Cải thiện và sửa một số lỗi.
      + Một số thay đổi có thể ảnh hưởng code:
        - $__HandleImgSearch_IsDebug -> $_HandleImgSearch_IsDebug.
        - $MaxImg mặc định 1000 nếu không khai báo.
    - 29/02/2020:
      + Sửa lỗi tìm handle sai khi sử dụng tên cửa sổ.
      
