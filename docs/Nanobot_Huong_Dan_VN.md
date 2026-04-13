# Tài Liệu Tổng Quan & Hướng Dẫn Cài Đặt `nanobot`

Tài liệu này được biên soạn nhằm giúp bạn hiểu rõ, nắm bắt toàn diện về dự án `nanobot`, một Trợ Lý AI Cá Nhân (Personal AI Agent) siêu nhẹ. Tài liệu cũng bao gồm hướng dẫn từng bước cấu hình đặc biệt dành riêng cho người mới bắt đầu lập trình và làm quen với Python.

---

## 1. Nanobot Là Gì? Những Điểm Nổi Bật
**`nanobot`** là một công cụ giúp tạo ra các Trợ lý AI có thể kết nối với rất nhiều nền tảng ứng dụng phổ biến, hỗ trợ các quy trình tự động.
- **Siêu gọn nhẹ (Ultra-lightweight):** Mã nguồn được thiết kế với số lượng dòng code cực ít, giảm 99% lượng code thừa so với các framework tạo AI Agent thông thường, giúp tốc độ phản hồi chớp nhoáng (Lightning Fast).
- **Trở thành Quản Gia đa kênh:** Bot có khả năng nói chuyện với bạn trên **Telegram, Discord, WeChat, Email, Slack, WhatsApp...** như một người thật ở trong danh bạ thay vì bạn phải thao tác trên một trang web.
- **Cấu trúc Mở / Dễ Học (Research-friendly):** Phù hợp để bạn học cách một Agent giao tiếp bằng lệnh, lưu giữ trí nhớ dài hạn hiệu quả.

---

## 2. Giải Đoán Các Công Cụ Cài Đặt: `uv` so với `PyPI (pip)`
Khi đọc trong tài liệu cài đặt, bạn thấy hai lựa chọn `Install with uv` và `Install from PyPI`. Đây là điểm dễ khiến lập trình viên mới phân vân:

### So Sánh
1. **PyPI (`pip`):** 
   - *Cách hoạt động:* Sử dụng lệnh `pip install nanobot-ai`. Đây là công cụ cài đặt mặc định của Python từ xưa tới nay.
   - *Rủi ro:* Cài đặt qua `pip` thường tải mọi thứ lên môi trường hệ thống chính. Nếu bạn đang chạy các phần mềm hay dự án Python khác, các thư viện (phần mềm con) mà `nanobot` sử dụng có thể sẽ bị **đụng độ (conflict)** lẫn nhau, gây lỗi không rõ nguyên nhân.
2. **`uv`:** 
   - *Cách hoạt động:* Sử dụng lệnh `uv tool install nanobot-ai`. Đây là công cụ hiện đại, tối tân, được viết bằng ngôn ngữ Rust để chạy với tốc độ cực kì nhanh.
   - *Bảo vệ:* Quan trọng nhất, lệnh `uv tool` sẽ tự động tạo một **"hộp kín" (môi trường ảo độc lập - isolated virtual environment)** dành riêng cho `nanobot`. Nó cài như một "ứng dụng độc lập hoàn chỉnh", không làm hệ thống máy tính của bạn bị xáo trộn.

### 💡 Lời Khuyên Bạn Nên Dùng Gì?
> Vì bạn chưa biết nhiều về Python, **tôi khuyên bạn BẮT BUỘC hãy sử dụng `uv`**. Lựa chọn này giúp mọi thứ trơn tru, không phát sinh lỗi cài đặt môi trường. Việc nâng cấp và xóa đi sau này cũng vô cùng sạch sẽ.

---

## 3. Hướng Dẫn Cài Đặt và Cấu Hình Từng Bước
Dành cho hệ điều hành **MacOS** của bạn. Hãy mở ứng dụng `Terminal` lên và làm theo trình tự dưới đây.

### Bước 3.1: Cài đặt công cụ `uv` (Nếu chưa có)
Trong cửa sổ Terminal, dán câu lệnh sau để cài đặt `uv`:
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```
*Lưu ý: Sau khi cài xong, bạn hãy TẮT hẳn cửa sổ Terminal đi, sau đó BẬT LẠI một Terminal mới để máy tính nhận dạng lệnh `uv`.*

### Bước 3.2: Cài đặt Ứng dụng `nanobot`
Dùng `uv` để tải phiên bản nanobot chính thức:
```bash
uv tool install nanobot-ai
```
Sẽ mất vài giây để máy tính tự động lấy toàn bộ thư viện về và bỏ vào hộp kín. Kiểm tra xem nanobot đã hoạt động chưa bằng lệnh:
```bash
nanobot --version
```

### Bước 3.3: Khởi tạo Thiết lập Ban Đầu
Bây giờ, chúng xuất câu lệnh sau trên cửa sổ Terminal để mở Trình thuật sĩ Cài đặt tự động:
```bash
nanobot onboard --wizard
```
Trình thuật sĩ sẽ hỏi bạn bằng một bảng lựa chọn tương tác đơn giản:
1. **Chọn Nhà Cung Cấp Model (Provider):** Bạn có thể chọn `groq` hoặc `gemini` để dùng cho tiện. Thường chuyên gia sẽ hay dùng **`openrouter`**.
2. **Điền API Key:** Bạn tạo API key tại trang web của nhà cung cấp đó ([ví dụ OpenRouter Key](https://openrouter.ai/keys)), sao chép và dán vào Terminal khi được hỏi.
3. Các thiết lập còn lại chỉ cần nhấn phím Enter để bỏ qua.

Lệnh này vừa tạo ra một File cấu hình ở trên máy bạn nằm tại đường dẫn: `~/.nanobot/config.json`.

### Bước 3.4: Trò chuyện và Thưởng thức
Đến đây bạn đã hoàn thành việc thiết lập. Hãy thử nói chuyện với Agent bằng lệnh:
```bash
nanobot agent
```
Hoặc chat và giao nhiệm vụ trực tiếp:
```bash
nanobot agent -m "Chào bạn, làm giúp tôi danh sách những việc cần làm buổi sáng!"
```

### Bước 3.5: Cài đặt Local Model (Ollama / vLLM) để bảo mật 100%
Nếu bạn đề cao quyền riêng tư tuyệt đối (không muốn gửi tin nhắn lên thiết bị/máy chủ của các tập đoàn thứ ba), bạn có thể trỏ bot tới **Ollama** hoặc **vLLM** hoạt động trên chính phần cứng của bạn!
- **Hỗ trợ Model nào?** Nanobot có kiến trúc đầu cuối mở đạt tiêu chuẩn OpenAI API. Nó hỗ trợ **TẤT CẢ các AI Models mã nguồn mở mà Ollama hoặc vLLM có thể chạy được** trên máy bạn (Ví dụ các dòng nổi tiếng như: `llama3.2`, `qwen2.5`, `mistral`, `deepseek-coder`, vv).

**Hướng dẫn với Ollama:**
1. Bật sẵn Ollama ở máy tính cấu hình của bạn kèm model (ví dụ model `llama3.2`):
```bash
ollama run llama3.2
```
2. Mở tệp tin `~/.nanobot/config.json` bằng text editor, thêm bổ sung đoạn mã ngắm bắn đường dẫn tới cổng thiết bị localhost của máy bạn:
```json
{
  "providers": {
    "ollama": {
      "apiBase": "http://localhost:11434"
    }
  },
  "agents": {
    "defaults": {
      "provider": "ollama",
      "model": "llama3.2"
    }
  }
}
```

**Hướng dẫn với vLLM:**
Cách làm hoàn toàn tương tự. Bạn chỉ cần sửa đường dẫn `"apiBase": "http://localhost:8000/v1"`, tên provider tuỳ ý và đổi `"model"` thành model mà vLLM máy bạn đang serve là thành công. Lúc này bot sẽ giao tiếp ở vòng kín Localhost không cần Internet!

---

## 4. Bổ Sung: Giải Trí Trên App Chat (Tuỳ chọn)
Nanobot không chỉ sống trên màn hình của Terminal. Bạn có thể cho nó một hình hài trên Ứng dụng Chat, ví dụ như **Telegram**:

1. Vào Telegram, tìm kiếm con bot tên là `@BotFather`. Gõ lệnh `/newbot` và đặt một cái tên cho Trợ lý của mình.
2. BotFather sẽ cung cấp cho bạn một dãy mã bảo mật **`BOT_TOKEN`**.
3. Bạn dùng Text Editor để mở file cài đặt `~/.nanobot/config.json` lên. Sửa lại cấu hình kênh Telegram thành:
```json
{
  "channels": {
    "telegram": {
      "enabled": true,
      "token": "Điền_bot_token_vào_đây",
      "allowFrom": ["ID_telegram_của_bạn"]
    }
  }
}
```
*(Mẹo nhỏ: ID Telegram dạng con số như `12345678`, bạn có thể lấy bằng cách chat với bot @userinfobot trên Telegram).*

4. Mở lại Terminal, khởi động kết nối với mạng của Telegram bằng lệnh:
```bash
nanobot gateway
```
Lúc này, hãy mở điện thoại lên, tìm đến app Telegram và gõ tin nhắn cho bot của bạn.

---

## 5. Phân Tích Cấu Trúc Mã Nguồn (Dành Cho Tương Lai Nếu Bạn Muốn Lập Trình)
Vì bạn quan tâm đến tổng quan về thiết kế dự án mã nguồn, dưới đây là "bản đồ giải phẫu" giúp bạn nếu mai sau bạn học Code sâu hơn:

- `nanobot/agent/`: Trái tim và bộ não của Agent. Đây là phần logic trò chuyện qua lại, lưu giữ lại lịch sử nội dung chat để gửi cho Trí tuệ nhân tạo (LLM).
- `nanobot/providers/`: Nơi định nghĩa các Cổng kết nối AI (OpenAI, Gemini, Anthropic, DeepSeek). Mã nguồn ở đây được thiết kế linh hoạt. Rất dễ thêm mô hình mới thay vì phải viết một đoạn mã nhùng nhằng dài dằng dặc.
- `nanobot/channels/`: Các con đường để bot tiếp xúc với con người (chứa code kết nối với API của Telegram, Feishu, Discord...). Thiết kế hướng sự kiện độc lập.
- `nanobot/cli/` & `nanobot/command/`: Trình biên dịch giúp nhận diện và diễn dịch lệnh gõ trên Terminal của bạn (như `/status`, `nanobot agent`).
- `nanobot/session/`: Phần hấp dẫn nhất liên lạc tới **Bộ Nhớ (Memory)**. Có cơ chế tự động tóm tắt nội dung thu gọn lại (Auto Compact) giữ thông tin cho con Bot thông minh nhớ bài toán bạn đang làm mà không tiêu tốn tiền API do tin nhắn quá giới hạn.
- `nanobot/cron/`: Bộ hẹn giờ lên lịch tự động cho các công việc.
- `nanobot/skills/` & `nanobot/tools/`: Các tiện ích plugin cho phép bot biết cách tự tra Google Search đọc nội dung web khi bạn đặt các câu hỏi ở sự kiện tương lai.

> **Tổng kết:** Hãy bắt đầu với `uv tool install nanobot-ai`, điền API Key tại `config.json`, thử nghiệm với lệnh Terminal... Bạn sẽ làm chủ hoàn toàn mã nguồn này một cách mượt mà nhất!

---

## 6. Đánh Giá Độ An Toàn Dữ Liệu
Về cấu trúc dự án `nanobot` là **Local-First / Privacy-First** (lưu dữ liệu cục bộ). Mọi thông tin hệ thống không bị đẩy lên đám mây trung gian:
- **Dữ liệu cục bộ:** API Key nhà cung cấp được lưu trên máy chủ của bạn (`~/.nanobot/config.json`). Bạn giữ quyền kiểm soát tệp này. Lịch sử trò chuyện (quản lý bởi module `nanobot/session`) lưu cục bộ và chia tách riêng biệt từng tệp cho từng người dùng.
- **Tiêu chuẩn An Toàn (Sandboxing):** Khi được cấp quyền đọc tệp và sử dụng Terminal, `nanobot` có bộ lọc phòng thủ chống lại các lệnh độc hại (`rm -rf /` hay `mkfs`). Đặc biệt, dự án hỗ trợ nhốt bot vào lồng kính Bubblewrap Sandbox (`bwrap`) chuyên biệt dành cho hệ thống điều hành Linux.
- **Duyệt qua Whitelist:** Tính năng Access Control sử dụng mảng danh sách trắng `allowFrom`. Mặc định người lạ nhắn tin cho Bot sẽ bị khước từ phục vụ và xoá bỏ quyền kết nối.
- **Cẩn trọng duy nhất:** Các tin nhắn của bạn được trung chuyển an toàn qua Internet (HTTPS) ra server của đơn vị cung cấp Trí Tuệ (Ví dụ OpenAI/ChatGPT/Google). Do đó tính riêng tư về LLM phụ thuộc vào chính sách hãng. Nếu bạn cần bảo mật quân sự độc lập 100%, hãy cài đặt mã nguồn chạy chung với một bot Local (qua phần mềm cục bộ **Ollama** tại nhà của bạn).

---

## 7. Khả Năng Hỗ Trợ Đa Tài Khoản (Multi-User)

Tuy tính cá nhân là cốt lõi nhưng dự án có chiều sâu để mở rộng việc kiểm soát đa người dùng (Công ty/Nhóm). 
- **Bộ nhớ độc lập:** Cuộc hội thoại của Người dùng A và Người dùng B có vách ngăn cách riêng trên thư mục làm việc. Mã hội thoại được tự định danh phân mảnh theo phương thức `channel:chat_id`. 
- **Chia sẻ Môi trường Thực Thi Lệnh (Workspace/Tools):** Nhưng nếu bạn cho nhiều account dùng chung MỘT phần mềm bot chạy duy nhất, họ sẽ bị **trùng lặp Không gian Dữ liệu Máy tính (Workspace)**. Nếu người A bảo AI tạo file lịch trình, bot có thể dễ dàng lấy nó đọc lên cho người B khi được sai khiến. 
- **Cách Triển Khai Tối Ưu (Multiple Instances):** Để cấp phát môi trường cho tổ chức, bạn chỉ cần chạy song song nhiều bảng ứng dụng (Instances). Bằng cách kích hoạt bot với tham số `-c` (chỉ định cấu hình) và `-w` (chỉ định vùng Workspace), bạn tạo ra các con bot độc lập tài nguyên 100% đối với nhau trên cùng một chiếc máy chủ!
```bash
# Đối với Khách Hàng (User A)
nanobot gateway -c ~/UserA_Bot/config.json -w ~/UserA_Bot/Workspace

# Đối với Khách Hàng (User B)
nanobot gateway -c ~/UserB_Bot/config.json -w ~/UserB_Bot/Workspace
```

---

## 8. Thông Tin Về Giao Diện Quản Quản Trị Hệ Thống (Web UI)
Hiện tại dự án **KHÔNG HỀ CÓ** trang Web Bảng điều khiển (Dashboard) hay Web UI nào.
Vì mang bản chất **Ultra-Lightweight Agent** — chú trọng cốt lõi, chạy ngầm siêu nhẹ và ưu tiên vận hành bằng dòng lệnh (Terminal-centric).
- Mọi thao tác đều nằm gọn bằng cách chỉnh sửa tệp `.json` khi cần thay đổi API hay Danh sách Trắng cấu hình mạng.
- **Dành cho Lập Trình Viên:** Nếu bạn dự định thương mại hoá, việc xây dựng một Panel Dashboard bằng React/Next.js trung tâm với chức năng viết sinh mã `config.json` và châm mồi các quá trình Terminal ngầm là một ý tưởng Web App mở rộng rất tốt với kiến trúc vốn có sẵn này.

---

## 9. Hạn Chế Nội Tại & Cách Xử Lý File Đính Kèm Nhị Phân (Excel)
Đây là một "Limit" (Hạn Chế) bạn bắt buộc phải biết khi thiết kế luồng Bot xử lý Email bằng mạng lưới của nanobot.
Vì tôn chỉ của dự án là siêu gọn nhẹ, file lõi hệ thống (`nanobot/agent/tools/filesystem.py`) chỉ được thiết kế để đọc các tệp nguyên bản **Văn bản Text (.txt, .md, .csv)**, **Hình ảnh** và **PDF**. Hệ thống lõi gốc **KHÔNG THỂ tự mở các tệp Nhị Phân (Binary) phức tạp** như tệp bảng tính `.xlsx` (Excel).

**Trường hợp luồng Email tới có kèm file Excel sẽ diễn ra quá trình sinh học như sau:**
1. **Lọc Input & Hút File:** Nếu thiết lập của bạn trong `config.json` có chấp thuận nhận định dạng Excel (`allowedAttachmentTypes`), hệ thống chìm của Bot sẽ tải file đính kèm đó về ổ cứng máy chủ và cất tại `~/.nanobot/media/`.
2. **Kịch bản Thất Bại (Nếu bạn xài Bot Nguyên Bản):** AI sẽ dùng lệnh mặc định gọi mở file Excel đó. File manager báo lỗi định dạng nhị phân chối từ phục vụ. Tuy bot không quét được, nhưng nhờ trí não linh động của LLM, nó sẽ tự động "sáng tạo" ra một lời hồi đáp Email/Thông báo về cho bạn nhằm thanh minh: *"Tôi xác nhận đã nhận Email Tờ trình. Tuy nhiên tệp đính kèm Excel nằm ngoài khả năng kỹ thuật của tôi, người dùng xin hãy cung cấp file PDF hoặc CSV!"*.
3. **Kịch bản Xử Lý Triệt Để (Khi Bot được gắn Modules):** Để khui hoàn hảo file `.xlsx`, bạn buộc phải nới rộng giới hạn hệ thống qua 3 phương hướng:
   - **Xử lý Đổi Chiều (Cách Dễ Nhất):** Thay vì nộp `.xlsx`, hãy đổi quy trình làm việc yêu cầu nội bộ chỉ lưu và gửi báo cáo dưới dạng **`.CSV`**. Công cụ gốc của bot đọc `.CSV` mượt mà vô hạn.
   - **Công Nghiệp Hoá bằng MCP:** Gắn thêm một Trạm công cụ đồ chơi thứ 3 qua giao thức chuẩn **MCP (Model Context Protocol)** chuyên trị đọc dữ liệu Data Science hoặc Excel. Bot sẽ ngầm mượn dao của MCP này để xả bảng tính.
   - **Viết Skill Lập trình bằng Python:** Viết một đoạn mã Python Pandas cực vi mô gắn vào thư mục mở rộng `nanobot/skills/`. Bot có thể chủ động đánh thức tệp script này để lôi số liệu Excel ra dịch thành dạng chuỗi Markdown. 
