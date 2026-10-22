# 🔎 Murdle · Thám Tử Đấu Trí

Trò chơi suy luận phá án cho **2 người** chơi online, tiếng Việt, chạy ngay trên trình duyệt.
Phỏng theo *Murdle* (sách giải đố của G.T. Karber và board game của Endless Games). Luật được chuyển thể để chơi online.
Hai thám tử **đấu trí**: ai buộc tội đúng hung thủ, hung khí và địa điểm trước thì thắng.

Chơi online: https://tranviethoang99.github.io/murdle/

## Cách chơi online
- Bấm *Tạo phòng*, chọn cỡ vụ án (3×3 dễ, 4×4 chuẩn, 5×5 khó), số lượt buộc tội và cách xử lý khi chia sẻ thiếu căn cứ, rồi gửi mã hoặc link cho người kia.
- Người kia nhập mã và bấm *Vào phòng*.
- Người tạo phòng phải **giữ tab mở**, vì máy chủ phòng giữ lời giải và nội dung thẻ của từng người.

## Luật tóm tắt
- Mỗi nghi phạm cầm đúng 1 hung khí và ở đúng 1 địa điểm, không ai trùng ai. **Biên bản hiện trường** (công khai) cho biết nơi tìm thấy thi thể hoặc hung khí gây án.
- **4 hồ sơ chứng cứ** (Lời khai, Pháp y, Camera, Mật báo), mỗi thẻ là một manh mối luôn đúng. Mặt sau thẻ ghi loại manh mối. Gộp tất cả thẻ thì chỉ còn đúng một lời giải.
- Mở đầu: mỗi người xem riêng 2 thẻ.
- Mỗi lượt chọn 1 việc:
  - **Chia sẻ ✓** lên bảng chung → tự chọn 1 thẻ chưa xem.
  - **Chia sẻ ✗** lên bảng chung → rút Thẻ Phát Hiện (1 thẻ ngẫu nhiên).
  - **Công khai 1 thẻ** đối thủ chưa xem → rút Thẻ Phát Hiện.
  - **Buộc tội**: đúng thì thắng. Sai thì mất 1 lượt buộc tội và lời buộc tội bị công khai. Hết lượt buộc tội là thua.
  - **Bí — điều tra thêm**: chỉ dùng được khi không còn gì để chia sẻ hay công khai → rút Thẻ Phát Hiện.
- Điều được chia sẻ phải là thứ bạn **chứng minh được** từ những gì mình biết, và phải là **thông tin mới** so với thông tin công khai. Máy tự kiểm tra, nên không thể nói dối hay đoán mò. Chia sẻ thiếu căn cứ thì mất lượt (hoặc được chọn lại, tuỳ cài đặt).

## Lưới suy luận
- Chạm ô để ghi chú riêng (trống → ✗ → ✓). Ghi chú lưu trên máy bạn. Có tuỳ chọn tự gạch ✗ hàng/cột khi đánh ✓.
- Token tròn ✓/✗ là bảng chung, chấm màu cho biết ai chia sẻ. ✗ mờ là hệ quả hiển nhiên từ ✓ chung.

## Kỹ thuật
Một file `index.html` duy nhất, kết nối P2P bằng [PeerJS](https://peerjs.com/), cùng khung với Mật Danh Duet, Quoridor, Azul.
Mỗi vụ án được sinh ngẫu nhiên: lời giải là hai hoán vị (nghi phạm → hung khí, nghi phạm → địa điểm). Manh mối được chọn dần sao cho số "thế giới khả dĩ" giảm đều, đến gần thẻ cuối mới còn đúng một.
Có 14 loại manh mối, gồm cả manh mối theo đặc điểm (chiều cao, tay thuận, màu mắt, chất liệu, nặng nhẹ, trong nhà hay ngoài trời).
Máy chủ phòng kiểm tra mỗi lần chia sẻ bằng cách duyệt mọi thế giới còn khớp với hiểu biết của người chơi.
Không có chế độ chơi với máy.
Chạy thử: `npx http-server murdle -p 5197`.
