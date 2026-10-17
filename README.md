🎨 Phần 1: Code Web Thiệp 20/10 (Giao diện 1 Ô Chat)
Tạo một file tên là index.html trong thư mục project trên GitHub và dán toàn bộ đoạn code dưới đây vào:
 <!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Gửi chị em 20/10 🌸</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background: linear-gradient(135deg, #ff9a9e 0%, #fecfef 99%, #fecfef 100%);
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        /* Khung chat chính */
        .chat-container {
            width: 380px;
            max-width: 90%;
            height: 520px;
            background: #ffffff;
            border-radius: 20px;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.15);
            display: flex;
            flex-direction: column;
            overflow: hidden;
        }

        /* Đầu khung chat */
        .chat-header {
            background: #ff6b81;
            color: white;
            padding: 15px;
            text-align: center;
            font-weight: bold;
            font-size: 1.1rem;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }

        /* Vùng hiển thị tin nhắn */
        .chat-box {
            flex: 1;
            padding: 20px;
            overflow-y: auto;
            display: flex;
            flex-direction: column;
            gap: 12px;
            background-color: #f9f9f9;
        }

        /* Bong bóng tin nhắn */
        .message {
            max-width: 80%;
            padding: 12px 16px;
            border-radius: 18px;
            font-size: 0.95rem;
            line-height: 1.4;
            animation: popIn 0.3s ease-out forwards;
        }

        .message.bot {
            background-color: #ffe6e8;
            color: #d63031;
            align-self: flex-start;
            border-bottom-left-radius: 4px;
        }

        .message.user {
            background-color: #ff6b81;
            color: white;
            align-self: flex-end;
            border-bottom-right-radius: 4px;
        }

        /* Ô nhập tin nhắn */
        .chat-input-area {
            display: flex;
            padding: 12px;
            background: #fff;
            border-top: 1px solid #eee;
        }

        .chat-input-area input {
            flex: 1;
            padding: 10px 15px;
            border: 1px solid #ddd;
            border-radius: 20px;
            outline: none;
            font-size: 0.9rem;
        }

        .chat-input-area button {
            background: #ff6b81;
            color: white;
            border: none;
            padding: 8px 18px;
            margin-left: 8px;
            border-radius: 20px;
            cursor: pointer;
            font-weight: bold;
            transition: background 0.2s;
        }

        .chat-input-area button:hover {
            background: #ee5253;
        }

        @keyframes popIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
    </style>
</head>
<body>

    <div class="chat-container">
        <!-- ĐỔI TÊN NGƯỜI GỬI TẠI ĐÂY -->
        <div class="chat-header">🌸 Anh Chàng Ẩn Danh 🌸</div>
        
        <div class="chat-box" id="chatBox">
            <!-- Tin nhắn chào mặc định -->
            <div class="message bot">Chào bạn! Chúc mừng ngày 20/10 nhé! ✨</div>
            <div class="message bot">Hãy nhập câu hỏi hoặc lời nhắn bất kỳ bên dưới để nhận bất ngờ nhé! 🎁</div>
        </div>

        <div class="chat-input-area">
            <input type="text" id="userInput" placeholder="Nhập lời nhắn..." onkeypress="handleKeyPress(event)">
            <button onclick="sendMessage()">Gửi</button>
        </div>
    </div>

    <script>
        // CẤU HÌNH CÁC CÂU TRẢ LỜI 20/10 TẠI ĐÂY
        const defaultResponses = 
            "Chúc bạn ngày 20/10 ngập tràn niềm vui, xinh đẹp và luôn hạnh phúc nhé! 💖",
            "Mong rằng mỗi ngày của bạn đều rạng rỡ như những bông hoa! 💐",
            "Chúc bạn gặt hái được thật nhiều thành công và nhận được vô vàn quà hôm nay! 🎁",
            "Bạn là một điều vô cùng đặc biệt! Chúc bạn ngày 20/10 thật tuyệt vời! 🌟"
        ;

        function sendMessage() {
            const input = document.getElementById('userInput');
            const chatBox = document.getElementById('chatBox');
            const text = input.value.trim();

            if (text === '') return;

            // 1. Hiển thị tin nhắn của người dùng
            const userMsg = document.createElement('div');
            userMsg.className = 'message user';
            userMsg.innerText = text;
            chatBox.appendChild(userMsg);

            input.value = '';
            chatBox.scrollTop = chatBox.scrollHeight;

            // 2. Trả lời tự động sau 0.8 giây
            setTimeout(() => {
                const botMsg = document.createElement('div');
                botMsg.className = 'message bot';
                
                // Lấy ngẫu nhiên 1 câu chúc từ danh sách
                const randomReply = defaultResponsesMath.floor(Math.random() * defaultResponses.length);
                botMsg.innerText = randomReply;
                
                chatBox.appendChild(botMsg);
                chatBox.scrollTop = chatBox.scrollHeight;
            }, 800);
        }

        function handleKeyPress(e) {
            if (e.key === 'Enter') {
                sendMessage();
            }
        }
    </script>
</body>
</html> 

📝 Phần 2: Nội dung README.md (Hướng dẫn chỉnh sửa chi tiết)
Nội dung dưới đây dành cho file README.md trên GitHub, giúp người dùng hoặc chính bạn biết cách tùy biến giao diện web chat theo ý muốn:
# 💌 Web Thiệp Chat Chúc Mừng 20/10

Ứng dụng nhắn tin gửi lời chúc 20/10 đơn giản, dễ thương dành tặng chị em phụ nữ!

---

## 🛠️ Hướng Dẫn Tùy Chỉnh (Chỉnh Sửa Code)

Bạn có thể dễ dàng thay đổi tên, lời chúc và màu sắc bằng cách mở file `index.html` và sửa các vị trí sau:

### 1. Thay đổi tên tiêu đề khung chat
Tìm đến dòng **35** (hoặc tìm chữ `chat-header`):
```html
<div class="chat-header">🌸 Anh Chàng Ẩn Danh 🌸</div>

👉 Đổi chữ Anh Chàng Ẩn Danh thành tên hoặc biệt danh của bạn.

2. Thay đổi tin nhắn chào ban đầu
Tìm các dòng tin nhắn mặc định trong thẻ <div class="chat-box">:
<div class="message bot">Chào bạn! Chúc mừng ngày 20/10 nhé! ✨</div>
<div class="message bot">Hãy nhập câu hỏi hoặc lời nhắn bất kỳ bên dưới để nhận bất ngờ nhé! 🎁</div>
👉 Sửa nội dung bên trong thẻ <div> thành lời mở đầu bạn muốn.

3. Thay đổi danh sách lời chúc tự động
Tìm đến phần JavaScript ở cuối file:
const defaultResponses = 
    "Chúc bạn ngày 20/10 ngập tràn niềm vui, xinh đẹp và luôn hạnh phúc nhé! 💖",
    "Mong rằng mỗi ngày của bạn đều rạng rỡ như những bông hoa! 💐",
    "Chúc bạn gặt hái được thật nhiều thành công và nhận được vô vàn quà hôm nay! 🎁",
    "Bạn là một điều vô cùng đặc biệt! Chúc bạn ngày 20/10 thật tuyệt vời! 🌟"
👉 Thêm, bớt hoặc chỉnh sửa các câu chúc trong cặp dấu ngoặc kép "".

4. Thay đổi màu nền chủ đề (Màu hồng)
Nếu muốn đổi sang gam màu khác, bạn tìm trong phần <style>:

Màu nền toàn trang: Tìm body { background: ... }

Màu thanh tiêu đề & nút gửi: Tìm .chat-header và .chat-input-area button (sửa mã màu #ff6b81).

🚀 Cách Bật Demo Trên GitHub Pages
Vào Settings của Repository trên GitHub.

 1 . Chọn mục Pages ở thanh menu bên trái.

2 . Ở phần Build and deployment -> Branch, chọn main (hoặc master) và nhấn Save.

3. Chờ 1 - 2 phút, GitHub sẽ cấp cho bạn một đường link trang web trực tuyến để gửi cho bạn bè!;
